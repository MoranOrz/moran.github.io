## 定义容器
以下代码中的 `changeName` 为容器名字

```lua
local params = {}
local containers = require("containers")
------------------------------------------------------------------------------------------------
params.changeName = {                           -- 此处修改 changeName
    widget =
    {
        slotpos = {},
        animbank = "ui_chester_shadow_3x4",     -- 容器的背景 UI 贴图
        animbuild = "ui_chester_shadow_3x4",    -- 容器的背景 UI 贴图
        pos = Vector3(0, 200, 0),               -- 容器的位置
        side_align_tip = 160,
    },
    type = "chest",     -- 容器的类型，结合下面参数 openlimit 限制整个世界里只允许有一个当前类型的容器被打开
    -- openlimit = 1,
    itemtestfn = function(inst, item, slot)     -- 限制进入容器内的物品的判断
        if item:HasTag("fresh") then
           return true
        end
        return false
    end
}
------------------------------------------------------------------------------------------------
for y = 2.5, -0.5, -1 do                        -- 遍历格子，此处修改 changeName
    for x = 0, 2 do
        table.insert(params.changeName.widget.slotpos, Vector3(75 * x - 75 * 2 + 75, 75 * y - 75 * 2 + 75, 0))
    end
end
------------------------------------------------------------------------------------------------
for k, v in pairs(params) do
    containers.MAXITEMSLOTS = math.max(containers.MAXITEMSLOTS, v.widget.slotpos ~= nil and #v.widget.slotpos or 0)
end
------------------------------------------------------------------------------------------------
local containers_widgetsetup = containers.widgetsetup
------------------------------------------------------------------------------------------------
function containers.widgetsetup(container, prefab, data)
    local t = prefab or container.inst.prefab
    if t == "changeName" then                   -- 此处修改 changeName
        local t = params[t]
        if t ~= nil then
            for k, v in pairs(t) do
                container[k] = v
            end
            container:SetNumSlots(container.widget.slotpos ~= nil and #container.widget.slotpos or 0)
        end
    else
        return containers_widgetsetup(container, prefab)
    end
end
```

## 客机添加容器
大佬说如果容器名 `changeName` 和 预设物 `prefab` 名相同的话，就不需要添加这一项  
但还是建议加上以免报错
```lua
if not TheWorld.ismastersim then
    inst.OnEntityReplicated = function(inst)
        inst.replica.container:WidgetSetup("changeName")    -- 此处修改 changeName
    end
    return inst
end
```

## 添加 container 组件
```lua
inst:AddComponent("container")
inst.components.container:WidgetSetup("changeName")         --此处修改 changeName
```