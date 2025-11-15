# Week 7 - BabySoC Physical Design & Post-Route SPEF Generation

## Reference Repos:
https://github.com/Akash-Perla/ASIC-Design?tab=readme-ov-file#task-13-OpenRoad-Physical-Design
https://github.com/vsdip/vsd-pd
 

 Steps I followed:
(Due to setup error in VM ubuntu i used codespaces on Github, faced similar issues  )
1. Launch the Codespace
Click Code → Codespaces → Create codespace on main

2. Wait for the setup to complete.
The log will show: “Finished configuring codespace.”

4. Run OpenROAD Flow Scripts
Once inside the Codespace terminal (or through the noVNC desktop terminal):
Here you go — **Markdown with bash code block**:

```bash
cd ~/Desktop
git clone https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts.git
cd OpenROAD-flow-scripts
sudo ./setup.sh
```

<img width="1920" height="1080" alt="Screenshot 2025-11-15 112318" src="https://github.com/user-attachments/assets/1bf041bf-227a-4c56-81a7-41abd331c1b0" />
<img width="1920" height="1080" alt="Screenshot 2025-11-15 120025" src="https://github.com/user-attachments/assets/de309530-af04-4f4d-b0ec-c0cf7467072a" />
<img width="1920" height="1080" alt="Screenshot 2025-11-15 120008" src="https://github.com/user-attachments/assets/359ba319-d1dc-4f67-b461-803ac2df4e70" />

```bash
./build_openroad.sh --local
```
Error
<img width="1920" height="1080" alt="Screenshot 2025-11-15 122503" src="https://github.com/user-attachments/assets/8ea82058-d8db-4f10-9238-b4a54c5d5282" />
Approach
<img width="1920" height="1080" alt="Screenshot 2025-11-15 122957" src="https://github.com/user-attachments/assets/076c8906-a267-4bf8-a5c9-daef498dcaf5" />
<img width="1920" height="1080" alt="Screenshot 2025-11-15 123056" src="https://github.com/user-attachments/assets/9eb6c772-1b00-4900-acfb-df96acd73490" />
Error:
<img width="1920" height="1080" alt="Screenshot 2025-11-15 123655" src="https://github.com/user-attachments/assets/52b628e6-fa3e-4307-bf4a-83c044cd5688" />
Approach:
<img width="1920" height="1080" alt="Screenshot 2025-11-15 123809" src="https://github.com/user-attachments/assets/0f5b7717-b83b-4f09-a71c-7b3fbe4620d3" />
<img width="1920" height="1080" alt="Screenshot 2025-11-15 132905" src="https://github.com/user-attachments/assets/601ecd9e-92a1-4c54-93a8-a346e39d0766" />

