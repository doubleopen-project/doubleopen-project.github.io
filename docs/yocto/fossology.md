# Get data from Fossology

## Upload source

For Fossology to be able to return licensing and copyright data for the source files, they need to
be uploaded to Fossology. The source archives to upload are filtered to exclude proprietary packages
from being scanned by not uploading source archive for the recipe if the license of the recipe
includes `CLOSED`.

Uploading is done with Double Open CLI with the following command:

```bash
doubleopen fossology -u <FOSSOLOGY_API_URI> -t <FOSSOLOGY_TOKEN> \
  upload \
  -f <FOSSOLOGY_FOLDER_ID> \
  --spdx <IMAGE_SPDX> \
  <SPDX_DEPLOY_DIR>/*.tar.bz2
```

## Populate SPDX

After the files have been scanned in Fossology, the SPDX Document of the image can be populated with
the data from the Fossology API. The API is queried with tha SHA256 hash values of the source files.
This is done with Double Open CLI with the following command:

```bash
doubleopen fossology -u <FOSSOLOGY_API_URI> -t <FOSSOLOGY_TOKEN> \
  query \
  -i <IMAGE_SPDX> \
  -o <OUTPUT_SPDX>
```
