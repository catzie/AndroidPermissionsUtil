# AndroidPermissionsUtil
Write less code for managing Android M permissions on your app

# Usage
Place PermissionsUtil.java in your project and update its package name accordingly. Instantiate object, set needed permissions, request code, and use the method allRequiredPermissionsGranted() to check if all required permissions have been granted.

Change "MainActivity" into the name of activity you're using this for.

Your activity should implement ```ActivityCompat.OnRequestPermissionsResultCallback``` and override ```onRequestPermissionsResult()```

## Example Usage:

```
private final int REQ_CODE_PERMS_FEATURE01 = 1;
String[] NEEDED_PERMS_FEATURE01 = { Manifest.permission.CAMERA, Manifest.permission.WRITE_EXTERNAL_STORAGE };

final PermissionsUtil permUtil = new PermissionsUtil(MainActivity.this);
permUtil.setNeededPermissions(NEEDED_PERMS_FEATURE01);
permUtil.setPermissionsRequestCode(REQ_CODE_PERMS_FEATURE01);

if(permUtil.allRequiredPermissionsGranted()){
    // proceed with what requires permission(s)
} else {
    permUtil.requestNeededPermissions();
}
```

##Example onRequestPermissionsResult()
```
    @Override
    public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
        if (requestCode == REQ_CODE_PERMS_FEATURE01) {
            Boolean permissionRequestResult = permUtil.processPermissionsRequestResult(requestCode, permissions, grantResults);
            if(permissionRequestResult){
                // proceed to do what needed permission(s)
            } else {
                // oops, user denied permission request
            }
        } else {
            super.onRequestPermissionsResult(requestCode, permissions, grantResults);
        }
    }
```
