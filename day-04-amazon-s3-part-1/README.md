# Day 4 - Amazon S3 Hands-on Lab (Part 1)

## Objective

Practice the core features of Amazon Simple Storage Service (S3), including bucket creation, object management, public and private access, presigned URLs, versioning, object transfer between buckets, and static website hosting.

---

## Services and Features Used

- Amazon S3
- S3 Buckets
- S3 Objects
- Object ACLs
- Presigned URLs
- Bucket Versioning
- Static Website Hosting
- Custom Index Page
- Custom Error Page
- Website Redirection

---

## Hands-on Tasks Completed

### 1. Created Amazon S3 Buckets

Created multiple S3 buckets in the Asia Pacific (Mumbai) region for practicing object storage and data transfer.

### 2. Uploaded Objects to S3

Uploaded files including text files, images, and PDF documents to S3 buckets.

### 3. Copied an Object Between S3 Buckets

Copied an object from one S3 bucket to another and verified that the object was successfully available in the destination bucket.

### 4. Configured Public Object Access

Modified object permissions to allow public read access and successfully accessed the object directly through a web browser.

### 5. Generated a Presigned URL for a Private Object

Generated a temporary presigned URL for a private S3 object and verified that it could be accessed without making the bucket or object permanently public.

### 6. Enabled S3 Versioning

Enabled bucket versioning, modified an existing file, uploaded it again with the same object key, and verified that multiple versions of the object were preserved.

### 7. Configured S3 Static Website Hosting

Enabled static website hosting on an S3 bucket and configured:

- Custom "index.html" page
- Custom "error.html" page
- Static website endpoint

Successfully accessed the hosted website through a browser.

### 8. Configured Website Redirection

Configured S3 static website hosting to redirect requests to another website and verified the redirection behavior.

---

## Key Learnings

- S3 stores data as objects inside buckets.
- Objects can be copied between different S3 buckets.
- Public access should be granted carefully and only when required.
- Presigned URLs provide temporary access to private objects without making them publicly accessible.
- Versioning protects against accidental overwrites and allows previous object versions to be retained.
- Amazon S3 can host static websites using HTML and CSS files.
- S3 website endpoints can also redirect requests to another website or domain.

---

## Screenshots

Screenshots of each configuration and verification step are available in the "screenshots" directory.

## Demo Videos

Video demonstrations of the custom static website index page and website redirection are available in the "videos" directory.

---

## Conclusion

This hands-on lab provided practical experience with core Amazon S3 functionality, including object management, access control, secure temporary sharing, versioning, cross-bucket object copying, and static website hosting.

This is Part 1 of my Amazon S3 hands-on practice. Part 2 will cover additional S3 security, storage management, lifecycle, replication, and advanced features.
