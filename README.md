# IoT-HW07
Assignment of IoT HW

BLE-Based Distance Estimation

Environment: Indoor corridor (minimal obstacles), temperature ≈ 22 °C

Hardware:

ESP32 BLE Server broadcasting at txPower = –59 dBm (measured at 1 m)

ESP32 BLE Client scanning and recording RSSI

Path-loss model:
![image](https://github.com/user-attachments/assets/c43fe021-8166-4ce7-8015-10aea0598fd3)

Procedure:

Place Server and Client at a fixed separation (0.5 m, 1 m, 2 m, 3 m, 4 m).

At each distance, record 10 RSSI samples on the Client.

Compute estimated distance for each sample via estimateDistance(rssi).

Calculate the mean estimated distance at each true distance.

Summary Table
True Distance (m)	Mean Estimated (m)	Error (m)	Error Rate (%)
0.5	                0.47	            0.03        	6.0
1.0  	              1.12	            0.12        	12.0
2.0  	              2.05	            0.05	        2.5
3.0  	              3.30	            0.30	        10.0
4.0                	3.90	            0.10	        2.5

bar chart
![output](https://github.com/user-attachments/assets/954e0fb2-be23-42b1-b69a-57eec556dd2e)

At distances of 2 m and 4 m, the BLE-based estimator achieved its best accuracy, with error rates as low as 2.5 %, whereas at 1 m and 3 m the deviations were larger—up to 10–12 %. Such variations are largely attributable to environmental factors: in our indoor corridor setting, multipath reflections cause the RSSI to fluctuate, and occasional human movement or slight changes in device orientation introduce additional noise. To improve overall performance, we recommend applying a moving-average filter to smooth out rapid RSSI spikes and, for even greater stability, incorporating a Kalman filter to dynamically correct measurement noise. Finally, gathering extra calibration data at intermediate points (for example at 1.5 m and 2.5 m) will allow you to refine both the txPower reference and the path-loss exponent n, further reducing systematic bias.


## HW07_1 : Server Code
![스크린샷 2025-05-15 033510](https://github.com/user-attachments/assets/a59c1c94-e963-4742-a91c-3ddd6117ae7b)

## HW07_2 : Client Code
![스크린샷 2025-05-15 033525](https://github.com/user-attachments/assets/22401039-39cb-461e-9c9e-fe95800f4b88)

## HW07_2_1 : Bouns 1 add
![스크린샷 2025-05-15 060145](https://github.com/user-attachments/assets/706b18c0-abf5-42ba-b6b6-aab644135f15)
![KakaoTalk_20250515_060257335](https://github.com/user-attachments/assets/c9fbc904-1ac9-4c3f-9a97-43ff1206b19a)

## HW07_2_2 : Bonus 2 add
![KakaoTalk_20250515_045954056](https://github.com/user-attachments/assets/0ec1a259-753e-4042-9d32-8b4bb0ce998b)



