<!--
{
  "title": "My computer wakes up from sleep mode, windows",
  "published": "November 08, 2024",
  "description": "My computer has been waken up sometimes from sleep mode. And I was always thinking maybe there's USB connection problem. However I found a real reason why it does that..."
}
-->

# My computer wakes up from sleep mode, windows

My computer has been waken up sometimes from sleep mode. And I was always thinking maybe there's USB connection problem. However I found a real reason why it does that.

If I `powercfg/lastwake` from cmd, I can check what caused it to wake up.

```
Wake History Count - 1
Wake History [0]
  Wake Source Count - 1
  Wake Source [0]
    Type: Wake Timer
    Owner: [SERVICE] \Device\HarddiskVolume3\Windows\System32\svchost.exe (SystemEventsBroker)
    Owner Supplied Reason: Windows will execute 'NT TASK\Microsoft\Windows\UpdateOrchestrator\Reboot_AC' scheduled task that requested waking the computer.
```

In my case, it was caused by the wake timer.

And I ended up disabling wake timer, because there's no such an important wake timer for personal computer.

```
Control Panel\Hardware and Sound\Power Options\Edit Plan Settings
```

Change advanced power setting -> Sleep -> Allow wake timers -> Disable