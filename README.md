# EDS
Purpose of the "Engineering Data System" is to provide a standard for naming parts, assemblies, drawings and other files thorugh their lifecycle. It includes features that speed up saving parts, inseritng parts in assemblies, interactive part filtering and exporting.

EDS can be used as standalone database filter or it can be used from Autodesk Inventor with the use of MACROS.

# Naming Schemes
Every name is made out of four sections:</br>
identifier-version-ID-revision</br>

Example:</br>
P-12-0012-002.ipt

### Section "identifier"
First letter or string of letters (in the above example: P) is used to identify type of file. There is a number of different file types in Inventor and below is a list of the most used file types and their labels:

P	-	part (.ipt)</br>
D	-	drawing (.dwg)</br>
SA	-	sub assembly (.iam)</br>
MA	-	main assembly (.iam)</br>
DW	-	drawing (.dwg)</br>
PR	-	presentation (.ipn)</br>

### Section "version"
Identifies the version which file belongs to. New version is considered to be every main assebly that is either being designed from ground up or has substantial changes. Every non substantial change is considered revision.

### Section "ID"
Describes unique part/assembly/drawing/etc... ID. It is automatically created by the script, should not be changed at any circumstances as it is used as the primary identifier inside database.

### Section "revision"
Identifies iteration/revision of the part.

It is important to note that section "version" and "ID" are in parent-child relationship, meaning that ID counter starts from 0 in each new version. Otherwise maximum number of unique part files is only 9,999.

#### Additional notes for parts
todo
#### Additional notes for assemblies 
todo

# Word about Inventor 2022 users
Inventor 2022 comes with a feature "Model states" and it's usage sould not be the same inside part files and inside assembly files. 

In parts:	Model states should be used to represent different phases in part production which later simplifies creating drawings. 
In assebblies:	Model states should be used to represent different revisions.

Not recommended usage is to use "Model States" for revisions inside the same part file. If "Model States" are used for revisions inside the same part file, model state tree gets unclear which in turn complicates part and drawing files tracking. 

When using mentioned approach, last section in "Naming Scheme" becomes obsolete for assembly files as different revisions are shown with the "Model States" in the assembly file itself but the naming scheme is fully kept the same.

# Folder naming and their purpose

<strong>If not otherwised noted, nested folders are ignored!</strong>

01-parts - <em>All .ipt parts here.</em><br>
02-sub_assemblies - <em>All .iam sub assemblies here.</em><br>
03-main_assemblies - <em>All .iam main assemblies here.</em><br>
04-drawings- <em>All .dwg drawings here.</em><br>
05-pdf - <em>All .pdf files.</em><br>
06-dxf - <em>All .dxf files.</em><br>
07-imported - <em>Imported files from TraceParts, GrabCAD, etc...  in raw/original filetypes (.step, .igs, etc..).</em><br>
08-FEM - <em>FEM reports here.</em><br>
09-simplified - <em>Shrinkwraps, derived parts, etc... go here.</em><br>
10-excel - <em>Excel files for driven parts/assemblies.</em><br>
11-renders - <em>Renders as .jpg, etc... create subfolders if using Keyshot or similar.</em><br>
12-representations - <em>All .ipn files here.</em><br>
13-exports - <em>Files that are not Inventor filetypes here.</em><br>
14-templates - <em>Put custom template files here (.dwg, .ipt, .iam, etc..).</em><br>

# Folder Structure
<pre>
.
├── parts
│   ├── P-01-0001-01 
│   ├── P-01-0001-02
│   ├── P-01-0002-01 
│   └── P-02-0001-01 
├── sub assemblies
│   ├── SA-01-0001-00
│   └── SA-01-0002-00
├── main assemblies
│   ├── MA-01-0000-00
│   └── MA-02-0000-00
├── eds.py 
└── project.ipj
</pre>
