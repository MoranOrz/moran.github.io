## 容器 UI 关闭动画残留的解决方案
> 1. 使用官方的 bank ，用自己的 build。(缺点，会有奇奇怪怪的问题，比如我的图片不见了。)
> 2. 反编译 anim.bin，删除 close 的最后一帧。然后复制删除后的最后一帧的一行到末尾，并加上斜杠。

**例如：**   
当然以下的原动画其实最后一帧我给删了。。。我是再复制了一遍倒数第二帧，拿来演示。  
反编工具皆来自 <b><font color="red">@五年一班</font></b>，由 <b><font color="red">@风铃草</font></b> 大佬提供的文件，非常感谢。
```xml
<!-- 原动画 -->
<anim framerate="40" name="close" numframes="6" root="ui_fridge_4x3">
    <frame h="382.0" w="550.0" x="0.0" y="0.0">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="1.0" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="337.0" w="550.0" x="0.0" y="-41.1407623291">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.762876987457" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="292.0" w="550.0" x="0.0" y="-82.2815093994">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.525754988194" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="247.0" w="550.0" x="0.0" y="-123.42225647">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.28863298893" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="202.0" w="550.0" x="0.0" y="-164.563018799">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.0515099987388" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="202.0" w="550.0" x="0.0" y="-164.563018799">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.0515099987388" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
</anim>
<!-- 修改后 -->
<anim framerate="40" name="close" numframes="6" root="ui_fridge_4x3">
    <frame h="382.0" w="550.0" x="0.0" y="0.0">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="1.0" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="337.0" w="550.0" x="0.0" y="-41.1407623291">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.762876987457" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="292.0" w="550.0" x="0.0" y="-82.2815093994">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.525754988194" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="247.0" w="550.0" x="0.0" y="-123.42225647">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.28863298893" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="202.0" w="550.0" x="0.0" y="-164.563018799">
        <element frame="0" layername="ui_fridge_4x3" m_a="1.0" m_b="0.0" m_c="0.0" m_d="0.0515099987388" m_tx="0.0" m_ty="0.0" name="ui_fridge_4x3" z_index="15"/>
    </frame>
    <frame h="202.0" w="550.0" x="0.0" y="-164.563018799"/>
</anim>
```