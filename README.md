Rather than re-create a new repo for these few small changes, I have opted to add what is needed to add build the Evolution ROM here and the reader will have to add them manually.

bootanimation.mk
#
# Copyright (C) 2019-2022 Evolution X
# Copyright (C) 2022 Raphielscape LLC.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

# Bootanimation
ifeq ($(TARGET_BOOT_ANIMATION_RES),1080)
     PRODUCT_COPY_FILES += vendor/evolution/bootanimation/bootanimation_1080.zip:$(TARGET_COPY_OUT_PRODUCT)/media/bootanimation.zip
else ifeq ($(TARGET_BOOT_ANIMATION_RES),1440)
     PRODUCT_COPY_FILES += vendor/evolution/bootanimation/bootanimation_1440.zip:$(TARGET_COPY_OUT_PRODUCT)/media/bootanimation.zip
else ifeq ($(TARGET_BOOT_ANIMATION_RES),720)
     PRODUCT_COPY_FILES += vendor/evolution/bootanimation/bootanimation_720.zip:$(TARGET_COPY_OUT_PRODUCT)/media/bootanimation.zip
else
    ifeq ($(TARGET_BOOT_ANIMATION_RES),)
        $(warning "Evolution X: TARGET_BOOT_ANIMATION_RES is undefined, assuming 1080p")
    else
        $(warning "Evolution X: Current bootanimation res is not supported, forcing 1080p")
    endif
    PRODUCT_COPY_FILES += vendor/evolution/bootanimation/bootanimation_1080.zip:$(TARGET_COPY_OUT_PRODUCT)/media/bootanimation.zip
endif

common.mk - just add these lines to their file
# Disable RescueParty due to high risk of data loss. The phone will stay booted unless this is here!!!
PRODUCT_PRODUCT_PROPERTIES += \
    persist.sys.disable_rescue=true

# Wifi-Calling from volte magisk module
PRODUCT_SYSTEM_DEFAULT_PROPERTIES += \
    persist.data.iwlan=1 \
    persist.data.iwlan.enable=true \
    persist.data.iwlan.ipsec.ap=1 \
    persist.dbg.ims_volte_enable=1 \
    persist.dbg.volte_avail_ovr=1 \
    persist.dbg.vt_avail_ovr=1 \
    persist.dbg.wfc_avail_ovr=1 \
    persist.nubia.5g.power.config=1 \
    persist.radio.calls.on.ims=1 \
    persist.radio.data_con_rprt=1 \
    persist.radio.data_ltd_sys_ind=1 \
    persist.radio.dynamic_sar=false \
    persist.radio.force_on_dc=true \
    persist.radio.NO_STAPA=1 \
    persist.radio.rat_on=combine \
    persist.radio.VT_HYBRID_ENABLE=1 \
    persist.rcs.supported=0 \
    persist.sys.strictmode.disable=true \
    persist.vendor.dpm.feature=1 \
    persist.vendor.radio.5g=1 \
    persist.vendor.radio.5g_mode_pref_0=1 \
    persist.vendor.radio.5g_mode_pref=1 \
    persist.vendor.radio.5g_mode_pref_1=1 \
    persist.vendor.radio.calls.on.ims=1 \
    persist.vendor.radio.data_con_rprt=1 \
    persist.vendor.radio.data_ltd_sys_ind=1 \
    persist.vendor.radio.enable_temp_dds=true \
    persist.vendor.radio.force_ltd_sys_ind=1 \
    persist.vendor.radio.force_on_dc=true \
    persist.vendor.radio.manual_nw_rej_ct=1 \
    persist.vendor.radio.mbn_load_flag=3 \
    persist.vendor.radio.mbn_wait_s=60 \
    persist.vendor.radio.redir_party_num=1 \
    ril.subscription.types=RUIM \
    ro.nubia.nr.support=1 \
    ro.telephony.default_cdma_sub=0 \
    ro.vendor.radio.5g=3
    
If you want to include the Bauhaus93 font, add these:
config/fonts.mk
    FontBauhaus93Overlay \
    
prebuilt/product/etc/fonts_customization.xml
    <!-- Bauhuas93 -->
    <family customizationType="new-named-family" name="bauhaus93">
        <font weight="100" style="normal">Bauhaus93.ttf</font>
    </family>
    <alias name="bauhaus" to="bauhaus93" weight="100" />
    
prebuilts/product/fonts/Bauhaus93.ttf
add the 'Bauhaus93.ttf" found in my repo

themes/fonts/FontBauhaus93SourceOverlay/res/values/config.xml
<!--
/**
 * Copyright (c) 2019, The Android Open Source Project
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *     http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */
-->
<resources xmlns:xliff="urn:oasis:names:tc:xliff:document:1.2">
     <!-- Name of a font family to use for body text. -->
    <string name="config_bodyFontFamily" translatable="false">bauhaus93</string>
    <!-- Name of a font family to use for medium body text. -->
    <string name="config_bodyFontFamilyMedium" translatable="false">bauhaus93-semi-bold</string>
    <!-- Name of a font family to use for headlines. If empty, falls back to platform default -->
    <string name="config_headlineFontFamily" translatable="false">bauhaus93</string>
    <!-- Name of the font family used for system surfaces where the font should use medium weight -->
    <string name="config_headlineFontFamilyMedium" translatable="false">bauhaus93-bold</string>
    <!-- Name of a font family to use as light font. For theming purpose. -->
    <string name="config_lightFontFamily" translatable="false">@string/config_bodyFontFamily</string>
    <!-- Name of a font family to use as regular font. For theming purpose. -->
    <string name="config_regularFontFamily" translatable="false">@string/config_bodyFontFamily</string>
</resources>


themes/fonts/FontBauhaus93SourceOverlay/res/values/strings.xml
<!--
/**
 * Copyright (c) 2019, The Android Open Source Project
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *     http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */
-->
<resources xmlns:xliff="urn:oasis:names:tc:xliff:document:1.2">
    <!-- Headline / Body font Bauhaus93 overlay -->
    <string name="font_bauhaus93_source_overlay" translatable="false">Bauhaus93</string>
</resources>



themes/fonts/FontBauhaus93SourceOverlay/Android.mk
#
#  Copyright 2019, The Android Open Source Project
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

LOCAL_PATH:= $(call my-dir)
include $(CLEAR_VARS)

LOCAL_RRO_THEME := FontBauhaus93Source
LOCAL_CERTIFICATE := platform
LOCAL_PRODUCT_MODULE := true

LOCAL_SRC_FILES := $(call all-subdir-java-files)

LOCAL_RESOURCE_DIR := $(LOCAL_PATH)/res

LOCAL_PACKAGE_NAME := FontBauhaus93SourceOverlay
LOCAL_SDK_VERSION := current

include $(BUILD_RRO_PACKAGE)

themes/fonts/FontBauhaus93SourceOverlay/AndroidManifest.xml
<!--
/**
 * Copyright (c) 2019, The Android Open Source Project
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 *
 *     http://www.apache.org/licenses/LICENSE-2.0
 *
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */
-->
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.android.theme.font.bauhaus93source"
    android:versionCode="1"
    android:versionName="1.0">
    <overlay android:targetPackage="android"
        android:category="android.theme.customization.font"
        android:priority="1"/>

    <application android:label="@string/font_bauhaus93_source_overlay" android:hasCode="false">
        <meta-data
            android:name="android.theme.customization.REQUIRED_SYSTEM_FONTS"
            android:value="bauhaus93,bauhaus93-semi-bold,bauhaus93-bold" />
    </application>
</manifest>

