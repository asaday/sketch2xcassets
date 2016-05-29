## sketch2xcassets

this script make xcassets from sketch

### Playground

andway, download this repo.

open sketch file and change something.  
save ⌘S  
open xcode and build ⌘B  
modefied sketch data is converted in xcassets!


### Prepare

1. install sketchtool.
	`/Applications/Sketch.app/Contents/Resources/sketchtool/install.sh`

2. copy sketch2xcassets.php to project folder.

	only you need file from this repo ,'sketch2xcassets.php'  
	other files is for demo.

3. prepare sketch file

	anyway run sketch and save it.

4. make xcassets to output

	New File -> Asset catalog, and enter name to output.  
	Xcode generate folder 'name.xcassets'

5. add runscript 

	```
	cd ${SRCROOT}
	php sketch2xcassets.php -gitignore Sample.sketch Sketch.xcassets Sketch.swift
	```
	add runscript TARGETS -> Build Phases  
	and move to under Target Depencies

6. build Xcode


### Script 

`sketch2xcassets.php [option] xxx.sketch xxx.xcassets`

#### xxx.sketch 

source sketch file.  
this script output slices.


#### xxx.xcassets

output folder.  
before run script, add xcassets in Xcode.

#### option

option|description
---|----
-pdf | generate PDF (default)
-png | generate PNG x1,x2,x3
-jpg | generate JPG x1,x2,x3
-gitignore | add gitignore in xcassets
-force | force convert


#### genetate swift code

`sketch2xcassets.php [option] xxx.sketch xxx.xcassets Sketch.swift`

Sketch.swift generated to easy access xcassets 


```
import UIKit

struct Sketch {
	static var Oval: UIImage { return UIImage(named: "Oval") ?? UIImage() }
	static var Polygon: UIImage { return UIImage(named: "Polygon") ?? UIImage() }
	static var Star: UIImage { return UIImage(named: "Star") ?? UIImage() }
}
```

you can use like this

```
view.addSubview(UIImageView(image: Sketch.Polygon))
```
