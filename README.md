# Cloudinary

A powerful media API for websites and mobile apps alike, Cloudinary enables developers to efficiently manage, transform, optimize, and deliver images and videos through multiple CDNs. Ultimately, viewers enjoy responsive and personalized visual-media experiences—irrespective of the viewing device.

## Use case

You have contractors that send you shootings and art, which you upload to Cloudinary. And then you learned that you could get them to upload assets directly to a designated folder using unsigned uploads, which is cool. Fewer emails, less effort, and no need for additional Cloudinary users.

But how should you use it? If you have development skills at your hand, and a ready infrastructure, you can go ahead and embed the Upload Widget instead of reading further down. This blog will show you how to unleash the power of unsigned uploads without a single line of code, and without a single ticket to the IT department.

## Prerequisites

You need to have a Cloudinary account or create one for [free Cloudinary account](https://cloudinary.com/users/register_free).

## Installing

### 1. Creating an unsigned upload preset

Use the [console](https://console.cloudinary.com/settings/upload) to define the options that apply to your uploads. We are going to modify 3 fields only to achieve our purpose, but there is much more functionality and value that can be explored in the [documentation](https://cloudinary.com/documentation/upload_presets#managing_upload_presets_using_the_settings_ui).
 - **Upload preset name** - The name is used to discern between your upload presets. It will not be shown in the minisite, but it is possible to see it when inspecting the HTML of the minisite.
 - **Signing Mode** - Change to unsigned. This allows unauthenticated users to upload assets.
 - **Folder** - Specify the Media Library folder you would like to have the uploaded assets. You don’t need to create this folder ahead, Cloudinary will create it for you upon the first upload.

### 2. Configuring the minisite
Edit the template [sample_uw.json](sample_uw.json) from this repo. At a minimum, edit these fields:
 - Title
 - Subtitle
 - uploadPreset - the one you used in the previous step

There are plenty of additional options to adjust like colors, fonts, and upload sources in the template.
Save the template using a meaningful public name, for example, “photographers.json”. Any name is valid, as long as the extension is kept “.json”.
Create a folder called “uploads_ministe” on the top-level folder of your environment. Upload the JSON file to this folder.
Adjust the public_id of the JSON file to match the folder structure, e.g. “uploads_ministe/photographers.json”.

### 3. Testing
Make sure that you can access the JSON from a web browser as 
ht<span>tps://\<your env id\>-res.cloudinary.com/raw/upload/uploads_minisite/photographers.json

### 4. Distributing
Immediately see the results at ht<span>tps://upload-minisite.cloudinary.us/\<your environment id\>/photographers.
