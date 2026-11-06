> [!IMPORTANT]
> **此 repo 已不再維護。** 這個 image 已移到 [swaglive/docker-images](https://github.com/swaglive/docker-images/tree/master/docker-google-cloud-storage)，
> 由 GitHub Actions 推到 `asia-docker.pkg.dev/swag-2c052/swaglive/google-cloud-storage`，之後的改動請到 docker-images 開 PR。
> 這裡的 publish workflow 已移除，Docker Hub 上的 `swaglive/google-cloud-storage` 不會再更新。
> 目前 docker-images 是直接沿用這裡最後一版 build 出來的 image。原本的建置方式還留在這個 repo，當作參考。（GENP-6287）

# Google Cloud Storage Proxy

Allows for access to Google Cloud storage with credentials automatically proxied into the request.

## Usage

* Currently uses Instance Metadata permissions for access to Google Cloud Storage
  * This means it inherits the permissions of the Instance when it was created (`scopes`)
  * Requires to be run in Google Cloud (or have access to the Google Instance Metadata API)
* The proxy will have access to any buckets/objects that the account has permission for (if it uses `storage-full` scope, then everything)

```
docker run -it --rm -p 80:80 swaglive/google-cloud-storage:0.1.0

curl http://127.0.0.1/my-bucket/hello/world.mp4
-> 200 OK
```

## REF
* https://cloud.google.com/storage/docs/downloading-objects

## TODO

* https://docs.nginx.com/nginx/admin-guide/content-cache/content-caching/#byte-range-caching
