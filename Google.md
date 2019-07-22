# GOOGLE MEMO

## GCS日本語名コピー

```Java
/** JsonFactory */
private static final JsonFactory JSON_FACTORY = JacksonFactory.getDefaultInstance();
/** HttpTransport */
private static final HttpTransport HTTP_TRANSPORT = new UrlFetchTransport();
/**  Scope */
private static final Set<String> SCOPES = StorageScopes.all();
/** Storage */
private Storage storage;

public void copy(String srcBucketName, String srcPath, String destBucketName, String destPath) throws IOException {
    storage = new Storage.Builder(HTTP_TRANSPORT, JSON_FACTORY, new AppIdentityCredential(SCOPES))
            .build();
    storage.objects().copy(srcBucketName,srcPath, destBucketName, destPath, new StorageObject()).execute();
}
```
