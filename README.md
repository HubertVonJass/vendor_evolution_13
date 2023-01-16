Rather than re-create a new repo for these few small changes, I have opted to add what is needed to add build the Evolution ROM here and the reader will have to add them manually.

replace Evo's with:
vendor/evolution/bootanimation/bootanimation.mk 
vendor/evolution/bootanimation/Android.mk 

add the contents from this to Evo's:
vendor/evolution/config/common.mk

If you want the Bauhaus93 font keep reading:
add the contents from this to Evo's:
vendor/evolution/config/fonts.mk
vendor/evolution/prebuilt/product/etc/fonts_customization.xml

add this file to this folder:
vendor/evolution/prebuilts/product/fonts/Bauhaus93.ttf

create the following directory structure:
themes/fonts/FontBauhaus93SourceOverlay/res/values/config.xml
themes/fonts/FontBauhaus93SourceOverlay/Android.mk
themes/fonts/FontBauhaus93SourceOverlay/AndroidManifest.xml
Add Android.mk, AndroidManifest.xml to FontBauhaus93SourceOverlay
add strings.xml & config.xml to themes/fonts/FontBauhaus93SourceOverlay/res/values
