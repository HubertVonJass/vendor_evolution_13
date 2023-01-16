Rather than re-create a new repo for these few small changes, I have opted to add what is needed to add build the Evolution ROM here and the reader will have to add them manually.

replace Evo's with:
vendor/evolution/bootanimation/bootanimation.mk 
vendor/evolution/bootanimation/Android.mk 

add the contents from this to Evo's:
vendor/evolution/config/common.mk

If you want the Bauhaus93 font keep reading:
    add the contents from these files to thoese from Evolution-X:
        vendor/evolution/config/fonts.mk
        vendor/evolution/prebuilt/product/etc/fonts_customization.xml
    add this file to this folder:
        vendor/evolution/prebuilts/product/fonts/Bauhaus93.ttf
    create the following directory structure:
    vendor/evolution/themes/fonts/FontBauhaus93SourceOverlay/res/values
        Add AndroidBauhaus.mk, AndroidManifest.xml to FontBauhaus93SourceOverlay. Change the name on AndroidBauahus.mk to just Android.mk
        add strings.xml & config.xml to themes/fonts/FontBauhaus93SourceOverlay/res/values
