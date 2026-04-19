
Step 1 — Extract & Build
bashunzip roblox_dumper.zip
cd roblox_dumper
make
This compiles everything into a binary called roblox_dumper.

Step 2 — Run
You must use sudo every time, otherwise macOS will block memory access.
bash# Most common — auto-finds Roblox and dumps to offsets.hpp
sudo ./roblox_dumper

# Wait for Roblox to launch, then auto-dump
sudo ./roblox_dumper --wait

# Custom output file
sudo ./roblox_dumper --out my_offsets.hpp

# Manual PID
sudo ./roblox_dumper --pid 12345

⚠️ Important — Before Running
The dumper finds offsets by scanning for specific float values defined at the top of dumper/dumper.hpp in the constant_find:: block, like:
cppconstexpr float HUMANOID_HEALTH = 87.3f;
constexpr float CAMERA_POSITION_X = 45.2f;
These need to match actual values in your running game. Before dumping, edit those constants to match your test place — e.g. set HUMANOID_HEALTH to your character's actual HP, set the camera position constants to where your camera actually is. Otherwise those offsets will show NOT FOUND.
