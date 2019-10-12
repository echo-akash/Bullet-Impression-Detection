<h1>Bullet Impression Detection</h1>
<h2>Objectives</h2>
<p>Determine bullet holes from firing target paper which will in return help to determine the MPI and zero any weapon(weapon correction).</p>
<h2>Procedure</h2>
<p>
<ol>
  <li>Data Collection(Images of Target Paper)</li>
  <li>If necessary you change the image resolution using transform_image_resolution.py</li>
  <li>Separate 80% of the images to train folder and 20% of the images to test folder.</li>
  <li>Label Bullet holes from target paper images(train folder images) using <a href="https://tzutalin.github.io/labelImg/">LabelImg</a> and assign class.</li>
  <li>Labeling the images will generate .xml file for each image. We need to convert all these .xml files to .csv files using xml_to_csv.py</li>
  <li>Convert .csv file to .record file using generate_tfrecords.py</li>
</ol>
</p>
