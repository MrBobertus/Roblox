```
local AudioModule = {}

-- Play sound at a specific part or in the workspace
function AudioModule.PlaySound(soundId, volume, fadeTime, loop, part, range)
	local sound = Instance.new("Sound")
	sound.SoundId = soundId
	sound.Volume = volume or 1
	sound.Looped = loop or false
	sound.MaxDistance = range or 100
	sound.RollOffMode = Enum.RollOffMode.Linear

	if part then
		sound.Parent = part
	else
		sound.Parent = game:GetService("SoundService")
	end

	sound:Play()

	if fadeTime then
		AudioModule.FadeIn(sound, fadeTime)
	end

	return sound
end

-- Stop a sound immediately or with a fade-out effect
function AudioModule.StopSound(sound, fadeTime)
	if fadeTime then
		AudioModule.FadeOut(sound, fadeTime)
	else
		sound:Stop()
		sound:Destroy()
	end
end

-- Set the volume of a sound
function AudioModule.SetVolume(sound, volume)
	sound.Volume = volume
end

-- Set the range of a sound
function AudioModule.SetRange(sound, range)
	sound.MaxDistance = range
end

-- Fade in a sound
function AudioModule.FadeIn(sound, fadeTime)
	local startVolume = 0
	local endVolume = sound.Volume
	sound.Volume = startVolume

	local step = (endVolume - startVolume) / (fadeTime * 60)
	while sound.Volume < endVolume do
		sound.Volume = sound.Volume + step
		wait(1 / 60)
	end

	sound.Volume = endVolume
end

-- Fade out a sound
function AudioModule.FadeOut(sound, fadeTime)
	local startVolume = sound.Volume
	local step = (startVolume - 0) / (fadeTime * 60)

	while sound.Volume > 0 do
		sound.Volume = sound.Volume - step
		wait(1 / 60)
	end

	sound.Volume = 0
	sound:Stop()
	sound:Destroy()
end

return AudioModule
```
