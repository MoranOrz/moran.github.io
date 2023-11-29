# 动画渐显
**例子来自：@幕夜之下**  
> 动画渐显效果，透明度从 0 一直到 100

```lua
local __transparency = 0
inst.AnimState:SetMultColour(1, 1, 1, __transparency)
inst.__SetMultColour_task = inst:DoPeriodicTask(FRAMES, function()
    __transparency = __transparency + 0.05
    if __transparency > 1 then
        __transparency = 1
        inst.__SetMultColour_task:Cancel()
    end
    inst.AnimState:SetMultColour(1, 1, 1, __transparency)
end)
```