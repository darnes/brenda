Multitask workout. 

Now, you can use project-name to configure sources location. With that you do not need to recreate config file, and restart instances.
Just putting config
DONE=poll
Will make instances running forever, pulling new projects from s3, and processing them.


TO Do so - first prep. your config.(you may see my config I used as example, and/or for test purposes. 

Direct configuration to root s3 bucket, 
BLENDER_PROJECT=s3://proj-input

next upload zipped sources to that location.

see proj-input directory - for idea on how that folder will eventually looks like.

New projects may be uploaded when other are in run - most important that task, that refer to it, must be added(see next section) after project upload. 
 

then, got to your project template, see proj1-template, and proj2-template
Now, format of the task is json, so template must be valid json, with 2 fields:
 * cmd - previous task(nothing changed here)
 * project-name - name of zipped folder, task is refers to.
 
see files above for the details.

```javascript
{
	"cmd": "blender -b proj1/*.blend -F PNG -o $OUTDIR/frame_###### -s $START -e $END -j $STEP -t 0 -a",
	"project-name": "proj1.tar.gz"
}
```

proj-output contents will give you idea how results will be stored.

Please do not hesitate to contact me in case you will have any questions, create issue here, or contact me directly via email: darnesmeister@gmail.com or skype: darnesmeister

 

