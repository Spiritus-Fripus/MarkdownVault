## Fonctions utiles pour le redimensionnement d'une image

```php
//-------------------
imagecreatefromgif();
imagecreatefrompng();
imagecreatefromjpeg();
// ------------------
getimagesize();
// ------------------
imagecreatetruecolor();
// ------------------
imagecopyresampled();
// ------------------
imagegif();
imagepng();
imagejpeg();
// ------------------
```

Dimension des images (aprés resize) :
1600 x 900
800 x 600
400 x 400
150 x 150

Astuces : partir de l'image resize 1600 x 900 , puis 800 x 600 , etc ...
1600 x 900 --> 800 x 600
800 x 600 --> 400 x 400
400 x 400 --> 150 x 150