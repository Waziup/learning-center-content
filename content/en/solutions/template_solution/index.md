---
title: DIY Plant Watering
desc: Keep your plants alive by automating the watering process.
architecture:
  resources:
    # ids are generated
    - id: 4dd1511f-4189-4253-9222-fcd51bac4d1c 
      type: Sensor_soilMoisture
      # rotation: 0, 90, 180 or 270
      rot: 0
      x: 0
      y: 0
      params: {}
    - id: 47ab828d-3871-450c-b8a1-3d41c09750de 
      type: Board_WaziDev
      rot: 0
      x: 100
      y: 0
      params: {}
    - id: 510efa71-66b1-4f5b-b49a-cc66c4048609 
      type: Actuator_relay
      rot: 0
      x: 50
      y: 50
      params: {}
    - id: b464747d-5882-4da3-b581-6a2507a92d63 
      type: Other_water_pump
      rot: 0
      x: 0
      y: 100
      params: {}
  lines:
    - from: 4dd1511f-4189-4253-9222-fcd51bac4d1c
      to: 47ab828d-3871-450c-b8a1-3d41c09750de
      color: "#ff0000"
      # x and y are the starting point of the line
      x: 0
      y: 0
      # l is the path of the line: horiz., vertic., ...
      l: [0, -10, 50, 10]
---