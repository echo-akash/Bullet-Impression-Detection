<h1>Bullet Impression Detection</h1>
<h2>Objectives</h2>
<p>Determine bullet holes from firing target paper which will in return help to determine the MPI and zero any weapon(weapon correction).</p>
<h2>Dependencies and Environment Setup</h2>
<p>
<ol>
  <li><a href="https://github.com/echo-akash/Python">Install</a> python along with pip.</li>
  <li>Download the <a href="https://github.com/echo-akash/Python/blob/master/PythonDependencySetup.bat">batch file</a> and execute it to install all the dependencies required.</li>
</ol>
</p>
<h2>Procedure</h2>
<p>
<ol>
  <li>Data Collection(Images of Target Paper)</li>
  <li>If necessary you change the image resolution using transform_image_resolution.py</li>
  <li>Separate 80% of the images to train folder and 20% of the images to test folder.</li>
  <li>Label Bullet holes from target paper images(train folder images) using <a href="https://tzutalin.github.io/labelImg/">LabelImg</a> and assign class.</li>
  <li>Labeling the images will generate .xml file for each image. We need to convert all these .xml files to .csv files executing xml_to_csv.bat</li>
  <li>Convert .csv file to .record file executing generate_tfrecords.bat</li>
  <li>Finally need to train the model by executing traincmd.bat file. The user can change the number of steps while training in faster_rcnn_inception_v2_pets.config file at line 113.</li>
  <li>About every 5 minutes the current loss gets logged to Tensorboard. We can open Tensorboard by executing open_tensorboard.bat file which will open a webpage at localhost:6006 and display the losses while training. You should train the model until it reaches a satisfying loss. The training process can then be terminated by pressing Ctrl+C.</li>
  <li>Now that we have a trained model we need to generate an inference graph, which can be used to run the model. For doing so we need to first of find out the highest saved step number. For this, we need to navigate to the training directory and look for the model.ckpt file with the biggest index. Now need to execute inf_graph_gen.bat file which will generate frozen_inference_graph.pb model at inference_graph folder and finally it will detect bullet holes from target image.</li>
</ol>
</p>
