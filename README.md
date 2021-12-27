# Lightweight PulseAudio Control

Since [marioortizmanero](https://github.com/marioortizmanero)'s [PulseAudio Control](https://github.com/marioortizmanero/polybar-pulseaudio-control) is causing a high load when in use with multiple sinks, ive written this lightweight version of it. The original would spike up to 100% cpu when used with 4 sinks (Ryzen 5 5600x) and this script uses about 10% at max.

# Significant Changes

  - dynamic sink support (+ different icons for every sink)
  - if a sink ceases to exist, this script only updates on card events, not everything
  - unimportant functions (for my use) have been removed for better performance

# Implementation

You can implement this too in a polybar module

    [module/pacontrol]

    type = custom/script
    tail = true
    label = "%output%"
    exec = path_to_script --listen your_sink_name
    scroll-up = path_to_script --up your_sink_name
    scroll-down = path_to_script --down your_sink_name
    click-left = path_to_script --togmute your_sink_name
    
or just call in a cli for testing

    ./script --listen your_sink_name
    
