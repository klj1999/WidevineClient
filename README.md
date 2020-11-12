# WidevineClient

The code was stolen from other people.

Anyway, it works. ^_^

---

## Sample

```C#
string initDataB64 = "AAAAW3Bzc2gAAAAA7e+LqXnWSs6jyCfc1R0h7QAAADsIARIQ62dqu8s0Xpa7z2FmMPGj2hoNd2lkZXZpbmVfdGVzdCIQZmtqM2xqYVNkZmFsa3IzaioCSEQyAA==";
string licenseUrl = "https://widevine-proxy.appspot.com/proxy";
var resp1 = PostData(licenseUrl, null, new byte[] { 0x08, 0x04 });
var certDataB64 = Convert.ToBase64String(resp1);
var cdm = new CDMApi();
var challenge = cdm.GetChallenge(initDataB64, certDataB64, false, false);
var resp2 = PostData(licenseUrl, null, challenge);
var licenseB64 = Convert.ToBase64String(resp2);
cdm.ProvideLicense(licenseB64);
List<ContentKey> keys = cdm.GetKeys();
foreach (var key in keys)
{
    Console.WriteLine(key);
}
```

## CDM Path

```
│  WidevineClient.exe
│  
└─cdm
   └─devices
       └─chrome_1610
              device_client_id_blob
              device_private_key
              device_vmp_blob
```

## Screen Shot

![image](https://user-images.githubusercontent.com/20772925/98831606-bec11d80-2476-11eb-97ee-cef03c73ab51.png)
