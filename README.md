# AndroidPermissionsUtil
Write less code for managing Android M permissions on your app

# Usage
Place PermissionsUtil.java in your project and update its package name accordingly. Instantiate object, set needed permissions, request code, and use the method allRequiredPermissionsGranted() to check if all required permissions have been granted.

## Example:

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
