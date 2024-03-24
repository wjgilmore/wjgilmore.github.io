---
layout: page
title: Disabling Axios SSL Validation
published: true
---

The NodeJS Axios library will by default verify the supplied server certificate against the associated certificate authority, which will fail if you're using a self-signed certificate. You can disable this behavior by setting `rejectUnauthorized` to `false` like so:

```
  const https = require("https");
  const httpsAgent = new https.Agent({ rejectUnauthorized: false });

  axios
    .post("https://app.screenshotlinks.com.test/api/screenshots", form, {
      httpsAgent,
      headers: {
        ...form.getHeaders(),
        // Authorization: "Bearer yourAuthToken", // If you need to send a token
      },
    })
    .then((response) => {
      console.log("Screenshot uploaded successfully:", response.data);
    })
    .catch((error) => {
      console.error("Error uploading screenshot:", error);
    });
```
