Modified:  Bob Bell, 8/18/2011
      Misc stuff to make it run better and to not have to assign values to as many variables.  the idea was to 
      eventually make this as portable as possible.

Modified:  Ralph Whaite, 8/17/2015
      Removed checking for the value of "*VERSION" in the parm file to determine 5010 or 4010.  In 2015, everything is 5010

Modified:  Ralph Whaite, 8/18/2015
      Added an option flag "dofield013".  Setting this option flag to "Y" will cause the script to run a process after the ANSI
      file is created to replace the BK with ABK as the code set identifier for ICD-10.  This will be most helpful for those who's
      ANSIP CMHC program is not up to current patch level with this functionality built in.  This process uses sed to replace a specific 
      text string "BK:ICD10:" with "ABK:".  This requires that the same flag "dofield013" be set in the ANSIDX10 script since this will 
      apply the necessary logic to create the string "BK:ICD10:" when sending the ICD-10 code.

This script will check to make sure specific bill files are not present before allowing the billing process
for a particular fund sournce to be run.  This will prevent a subsequently run billing process from replacing
a production bill file with another file of the same name before the file has been submitted and archived.

This script relies on the BillParm name being placed in the Add Parm1 menu item.  It uses this ParmFile name to get the file
name to check.

It also dynamically creates the ANSI 837 parmfile tells the ANSI process to process as version 5010

Lastly, if any special file edits need to be completed on the file before submission (ie: Texas LTC TypeAB KX Modifer)
A UNIX Command can be defined that will make those changes to the file.  Otherwise, do not set a value for the 
variable "FixCMD"

