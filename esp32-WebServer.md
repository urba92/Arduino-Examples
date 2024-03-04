```cpp
// Initialize LittleFS
TRACE("[INFO] Mounting LittleFS...\n");
if (!LittleFS.begin()) {
  TRACE("[ERROR] Failed to mount LittleFS\n");
  delay(2000);
  TRACE("Formatting...\n");
  LittleFS.format();
  delay(2000);
  TRACE("Restarting...\n");
  delay(2000);
  ESP.restart();
} else {
  TRACE("[OK] LittleFS mounted successfully\n");
}
```

```cpp
// Connect to Wi-Fi
TRACE("[INFO] Trying to connect to Wi-Fi");
WiFi.mode(WIFI_STA);
WiFi.begin(ssid, password);
uint8_t attempt = 0;
while (WiFi.status() != WL_CONNECTED) {
  delay(attemptInterval);
  TRACE(".");
  if (++attempt > maxAttempts) {
    Serial.print("\nFailed to connect to Wi-Fi");
    while (1) {
      delay(1000);
    }
  }
}
TRACE("\n[OK] Connection to Wi-Fi successful\n");
TRACE("[INFO] IP address: %s\n", WiFi.localIP().toString().c_str());
```
