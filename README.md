# fpdf_label
PSR implementation of http://www.fpdf.org/en/script/script29.php

Requires `php5-gd` and `php-fpdf` 

Usage:

```
use tjbenson\PDF_Label;
require_once('fpdf.php');
require_once('./vendor/autoload.php');

/*------------------------------------------------
To create the object, 2 possibilities:
either pass a custom format via an array
or use a built-in AVERY name
------------------------------------------------*/

// Example of custom format
// $pdf = new PDF_Label(array('paper-size'=>'A4', 'metric'=>'mm', 'marginLeft'=>1, 'marginTop'=>1, 'NX'=>2, 'NY'=>7, 'SpaceX'=>0, 'SpaceY'=>0, 'width'=>99, 'height'=>38, 'font-size'=>14));

// Standard format
$pdf = new PDF_Label('L7163');

$pdf->AddPage();

// Print labels
for($i=1;$i<=20;$i++) {
    $text = sprintf("%s\n%s\n%s\n%s %s, %s", "Laurent $i", 'Immeuble Toto', 'av. Fragonard', '06000', 'NICE', 'FRANCE');
    $pdf->Add_Label($text);
}

$pdf->Output('./output-file.pdf');
```
