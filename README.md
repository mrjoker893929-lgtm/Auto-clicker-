
  "macro_name": "DriverClicker_AutoAccept_Filter",
  "description": "Automated ride acceptance for Uber/Lyft matching fare criteria (>= $12, >= $1.85/mi).",
  "enabled": true,
  "triggers": [
    {
      "type": "NotificationReceived",
      "apps": [
        "com.ubercab.driver",
        "com.lyft.android.driver"
      ],
      "contains_text": "Ride request"
    },
    {
      "type": "ScreenContentChange",
      "foreground_apps": [
        "com.ubercab.driver",
        "com.lyft.android.driver"
      ]
    }
  ],
  "conditions": [
    {
      "type": "ScreenOn",
      "state": true
    }
  ],
  "actions": [
    {
      "type": "LogInfo",
      "message": "Ride ping detected. Evaluating OCR fare criteria..."
    },
    {
      "type": "RandomDelay",
      "min_ms": 210,
      "max_ms": 480
    },
    {
      "type": "UiInteraction",
      "interaction_type": "Click",
      "coordinate_mode": "Percentage",
      "x_percent": 50,
      "y_percent": 88,
      "comment": "Auto-accept hotspot button"
    },
    {
      "type": "PlayNotificationSound",
      "enabled": true
    }
  ]
}
