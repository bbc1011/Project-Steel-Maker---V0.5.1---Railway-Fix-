# Railway deployment notes

## Fix for `libxcb.so.1`

Railway runs a headless Linux container. Use:

    ultralytics-opencv-headless>=8.3

instead of the regular desktop `ultralytics` package.

The Python import remains unchanged:

    from ultralytics import YOLO

Do not install both `opencv-python` and `opencv-python-headless` together.

## If Railway still reuses the old dependency layer

Temporarily add this Railway variable:

    NO_CACHE=1

Redeploy once. After a successful clean build, you can remove `NO_CACHE`.

## Secrets

Keep API credentials in Railway -> Service -> Variables.
Do not commit a real `.env`.
