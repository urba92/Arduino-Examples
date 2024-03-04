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
