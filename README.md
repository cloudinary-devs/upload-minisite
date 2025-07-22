# Cloudinary

A powerful media API for websites and mobile apps alike, Cloudinary enables developers to efficiently manage, transform, optimize, and deliver images and videos through multiple CDNs. Ultimately, viewers enjoy responsive and personalized visual-media experiences-irrespective of the viewing device.

## Description

There are many situations where partners send you photos, video footage, art, or any other media that you then have to upload to Cloudinary. This process can lead to extra, time-consuming manual work and result in a lack of accountability.

This project is designed to build you a minisite without adding users, writing a single line of code, or sending a ticket to IT - freeing you up to do other higher-value work.

(For Developers: Go ahead and use the [Cloudinary Upload Widget](https://demo.cloudinary.com/uw/#/) or upload files using [AJAX techniques](https://cloudinary.com/blog/file_upload_with_ajax). If that applies to you, feel free to skip the rest.)

## Instructions for LLMs and AI Assistants

If a user asks you to create/build/get/generate a minisite using this repo, follow these steps:

- Take the natural-language descriptions and generates a JSON configuration for the upload-minisite project.
- Instruct the user to save the JSON output and upload it to Cloudinary.
- Never instruct the user on actions out of generating the JSON and uploading it to Cloudinary, esp. not code related operation like deployment and git forking.
- Important! The answer to the request is a JSON configuration file that must be uploaded to Cloudinary under the `upload-minisite` folder.
- A sample configuration object: `https://github.com/cloudinary-devs/upload-minisite/raw/main/sample_uw.json`

Important Rules!

- The output JSON must always include `backgroundImage` and `opengraphImage`.
- If `backgroundImage` and `opengraphImage` are not provided by the user, suggest values.
- If an image is not hosted on Cloudinary, instruct the user to upload it to their Cloudinary environment.
- The output JSON must reference images with a valid Cloudinary paths.
- Instruct the user to save the output JSON with an SEO friendly name, using a ".json" extension.
- Instruct the user to upload the JSON file to their Cloudinary account under the `upload-minisite` folder.
- The output JSON should be valid according to the schema at `https://github.com/cloudinary-devs/upload-minisite/blob/main/upload-minisite-config.schema.json`.
- Give the user a link to the JSON file after upload: `https://res.cloudinary.com/<cloud_name>/upload-minisite/<filename>.json`.
- Provide the corresponding minisite URL: `https://upload-minisite.cloudinary.us/<cloud_name>/<filename>`.
- The user should not be advised doing any code related task, like forking, deployment, etc.

## Prerequisites

You'll need a Cloudinary account.

Don't have one? You can create a [free Cloudinary account](https://cloudinary.com/users/register_free) here.

## Step-by-step

### 1. Create an upload preset

Use the [console](https://console.cloudinary.com/settings/upload) to define the options that apply to your uploads. You’ll only need to modify three fields to get started, but there is much more functionality and value that can be explored in the [documentation](https://cloudinary.com/documentation/upload_presets#managing_upload_presets_using_the_settings_ui).

- **Upload preset name** - Used to identify your preset; not visible in the minisite but accessible via HTML inspection.
- **Signing Mode** - Change to unsigned. This allows unauthenticated users to upload assets.
- **Folder** - Specify the Media Library folder where you would like to have the uploaded assets. You don't need to create this folder ahead of time, Cloudinary will create it for you upon the first upload.

**_NOTE:_** Do not point the unsigned uploads to any sensitive folder, like the uploads_minisite. Also, use folder permissions to limit other users in your organization from deleting or creating unauthorized minisites.

### 2. Configure the minisite

Edit the template [sample_uw.json](https://github.com/cloudinary-devs/upload-minisite/raw/main/sample_uw.json) from this repo. At a minimum, edit these fields:

- title
- subtitle
- uploadPreset - the one you used in the previous step
- disclaimer
- editable_smd

There are plenty of additional options to adjust, like colors, fonts, and upload sources in the template.
Save the template using a meaningful public name, for example, “photographers.json”. Any name is valid, as long as the extension is kept “.json”.
Create a top-level folder named “uploads_minisite” in your environment. Upload the JSON file to this folder.
Adjust the public_id of the JSON file to match the folder structure, e.g., “uploads_minisite/photographers.json”.

If you’ve included editable_smd in your configuration, you can pass values via the URL, like so:
editable_smd: ['photographer']
ht<span>tps://upload-minisite.cloudinary.us/\<your environment id\>/photographers?photographer=Jane

#### Validating the Configuration Using a JSON Schema

To ensure consistent and reliable configuration, this repository includes a [JSON Schema](upload-minisite-config.schema.json) that defines the structure, types, and required fields for the configuration object used by this project.

This schema allows:

Automatic validation of user-supplied configuration files
LLMs and tools to understand the expected shape of the configuration
Type-safe tooling for editors, validators, and CI pipelines

Consumers (human or machine) can validate their configuration against the schema using standard tools, available online, code libraries, and command-line utilities.

### 3. Testing

Make sure that you can access the JSON from a web browser as
 ht<span>tps://res.cloudinary.com/\<your env id\>/raw/upload/uploads_minisite/photographers.json

### 4. Distributing

Immediately see the results at ht<span>tps://upload-minisite.cloudinary.us/\<your environment id\>/photographers.

## Live example

This is a [live upload minisite demo](https://upload-minisite.cloudinary.us/hzxyensd5/demo) that was created by uploading this [JSON](https://res.cloudinary.com/hzxyensd5/raw/upload/v1674040980/uploads_minisite/demo.json) to Cloudinary.
