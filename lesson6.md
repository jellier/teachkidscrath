# 第六课：打地鼠

## 课程概括：   
> 这是一款非常有趣的打地鼠游戏。游戏的规则很简单，把冒出头来的地鼠给全部打下去就算成功。锤子跟随鼠标移动，点击鼠标锤子落下     
> 角色：地鼠，锤子，地洞    
>> 地鼠：1）增加一个被打中的造型 2）随机冒出来 3）被锤子打到的时候切换造型    
>> 锤子：1）跟随鼠标移动  2）打地鼠   
>> 地洞：克隆版本的游戏中才有代码   
>> 舞台：页面变量初始化，控制几号地鼠出现   

![打地鼠游戏](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster.jpg)


## 本节课涉及到的知识点、使用到的模块：  
> 虚像特效：在scratch中，虚像就是让图像变透明，虚像的值就是图像透明的程度     
  试试看：外观---> 将"颜色"特效设定为*** --> 点击"颜色"下拉框选择"虚像"--> 分别设置成10和100，看看差别
![虚像](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_virtual.jpg)

## 开始练习：
### 打地鼠      
> 说明： 用鼠标控制锤子的位置，将随机出现的地鼠打下去     
> 知识点：虚像，复杂的条件组合     
> 示例地址：[打地鼠：https://scratch.mit.edu/projects/325454314/editor](https://scratch.mit.edu/projects/325454314/editor)   
> 步骤：
>> step1. 添加背景、角色：   
        1）添加一个荒漠的背景     
        2）在"选择一个角色"中选择squirrel作为地鼠的形象，角色名为hamter1     
        3）画一个锤子：   
            A. 用两个椭圆和一个长方形拼成锤子头，一个长方形作为锤子柄，组合后旋转到适当角度     
            B. 选中造型选项卡，在造型1上点鼠标右键选择"复制"，Ctrl+A 全选中锤子的全部，然后拖动最下方的小弧线旋转图像，调整到合适位置，模拟锤子下落的造型   
        ![锤子](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_hammer.jpg) 
        4）画一个地洞：画两个同样形状但大小不同的椭圆，重叠到一起，留个边缘让地洞有立体感    
        ![地洞](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_hole.jpg)  
        5）复制5个地鼠，5个地洞     
        
>> step2. 给地鼠添加显示代码，模拟地鼠出现    
        1）当绿旗被点击：    
           A. 地鼠外观初始化：隐藏（游戏开始时所有地鼠都是隐藏在地洞里的）；移到最前面；移到相应位置；换成正常造型；将虚像特效设定为100     
           B. 让地鼠间隔一段时间显示：重复执行5次--> 将虚像特效增加-20；将y坐标增加2        
           备注：虚像可以实现一个图像由浅入深显示的效果。当虚像=0时，图像正常显示；当虚像=100时，图像完全透明。这个例子中虚像初始值为100（完全透明），在循环中每次增加-20，5次后虚像为0（正常显示）     
![地鼠1](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_hamster1.jpg)            
        
>> step3. 给舞台添加代码，控制5只地鼠随机出现    
        1) 添加一个变量"哪只地鼠出现"      
        2) 当绿旗被点击：每间隔1秒从1-5之中随机选一个数，给"哪只地鼠出现"赋值，并发送广播给相应的地鼠      
![舞台](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_storage.jpg)         
>> step4. 调整地鼠的代码    
        1）当接收到*号地鼠出来的广播：此地鼠显示     
        2）将原来绿旗下的代码放到接收广播的控制下方   
        3）当绿旗被点击：地鼠隐藏；切换成默认（正常）造型     
![地鼠2](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_hamster2.jpg)          
>> step5. 给锤子添加代码，鼠标跟随，模拟打的动作，以及触碰的检测     
        1）初始化：按造型1显示（锤子有两个造型，造型1是落下前的样子，造型2是落下后的样子）   
        2）重复执行：移到"鼠标指针"，实现鼠标跟随效果     
        3）模拟锤子落下效果：在循环中检测"如果按下鼠标？那么..." ，当锤子落下切换成"造型2"，等待0.2秒后，再切换回"造型1"     
            备注：因为锤子起落是一个完整的动作，落下还会抬起    
        4）碰撞检测：5只地鼠，所以在"如果。。。那么。。。"中需要用"**或**或**或**或**"来检测每一只地鼠是不是与锤子碰着    
        5）增加一个"得分"变量，每次打到地鼠加1分    
        6）广播"打到地鼠了"   
        7）得分后等待0.2秒，避免打一下得很多分   
![锤子](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_hammercode.jpg)            
>> step6. 调整地鼠的代码   
        1）地鼠接收到"打到地鼠了"的广播后切换到造型2    
        备注：这样的效果是一只被打到其他所有地鼠都要被打烂，但与此同时其他地鼠是隐藏的，而且每次地鼠出现的时候有一个造型的初始化，保证地鼠出现的时候是正常的样子，所以这里即使全部打烂也不影响。    
![地鼠2](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_hamster3.jpg)                 
>> step7. 调整和完善代码
        1）在每只地鼠收到显示的广播后加上"等待2秒"来控制游戏的节奏   
        2）增加game over 或者 You win 提示。
        
    

### 此示例扩展：打地鼠克隆版     
> 示例地址：[打地鼠--克隆地鼠地洞版：https://scratch.mit.edu/projects/326389786/editor](https://scratch.mit.edu/projects/326389786/editor)     
> 说明：之前的示例中5只地鼠除了序号不一样，其他都一样，每次修改代码，每只都要改一遍，很麻烦对不对？用学过的克隆方法，把一件事放在一个角色上解决。     
> 步骤：
>> step1. 添加背景、角色：   
        1）添加一个荒漠的背景     
        2）在"选择一个角色"中选择squirrel作为地鼠的形象，角色名为hamter1     
        3）画一个锤子：   
            A. 用两个椭圆和一个长方形拼成锤子头，一个长方形作为锤子柄，组合后旋转到适当角度     
            B. 选中造型选项卡，在造型1上点鼠标右键选择"复制"，Ctrl+A 全选中锤子的全部，然后拖动最下方的小弧线旋转图像，调整到合适位置，模拟锤子下落的造型    
        4）画一个地洞：画两个同样形状但大小不同的椭圆，重叠到一起，留个边缘让地洞有立体感    

>> step2. 锤子   
![克隆-锤子](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_clone_hammer.jpg)

>> step3. 克隆地洞
        1）增加一个变量"第几个地洞"，作为克隆地洞时的临时计数器，新建变量时默认选择"适用于所有角色"。  
        2）将地洞移到页面偏左的位置，重复执行5次"克隆自己"   
        3）调整克隆体的位置，在"克隆自己"前加上定位：   
            A. 调整地洞纵向位置，当前地洞的大小一排能摆下3个地洞，所以当地洞 < 4个，地洞放在第一行，> 4个，放到第二行，通过调整Y坐标实现行的排列    
            B. 当地洞 > 4个需要把第4个地洞放到第二行靠左的位置，所以当地洞 = 4时，把地洞的X坐标设为-190（X坐标范围 -240 -- 240 ）     
        4）为了能统一操作克隆体，将原型地洞隐藏  
        5）"当作为克隆体启动时" 新建一个"适用于当前角色"的变量"地洞编号"，并将"地洞编号"设定为"第几个地洞"（将全局变量的值赋给私有变量，用于操控克隆体） 
![克隆-地洞](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_clone_hole.jpg)
>> step4. 克隆地鼠        
        1）增加一个变量"第几只地鼠"，作为克隆地鼠时的临时计数器，新建变量时默认选择"适用于所有角色"。  
        2）将地鼠移到页面偏左的位置，在"当绿旗被点击"下，重复执行5次"克隆自己"   
        3）调整克隆体的位置，在"克隆自己"前加上定位，根据地洞的位置设定地鼠的位置，地鼠个数的判断及XY设定参照地洞   
        4）为了能统一操作克隆体，将原型地鼠隐藏   
        5）"当作为克隆体启动时" 给地鼠设定为默认造型，新建一个"适用于当前角色"的变量"地鼠编号"，并将"地鼠编号"设定为"第几只地鼠"（将全局变量的值赋给私有变量，用于操控克隆体）
![克隆-地鼠1](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_clone_hamster1.jpg)        
>> step5. 给舞台添加代码，控制5只地鼠随机出现    
        1) 添加一个变量"哪只地鼠出现"      
        2) 当绿旗被点击：每间隔1秒从1-5之中随机选一个数，给"哪只地鼠出现"赋值，并且广播"地鼠出来" 
          
>> step6. 给地鼠添加广播代码
        1）当接收到"地鼠出来"的广播，需要判断 --> 如果"哪只地鼠出现" == 地鼠编号，那这只地鼠出来
            A. 地鼠外观初始化：隐藏（游戏开始时所有地鼠都是隐藏在地洞里的）；移到最前面；移到相应位置；换成正常造型；将虚像特效设定为100     
           B. 让地鼠间隔一段时间显示：重复执行5次--> 将虚像特效增加-20；将y坐标增加2   
           C. 将和锤子的触碰判断放到地鼠克隆体上来处理 ，如果碰到锤子广播"打到地鼠了"
           D. 地鼠显示后等待0.5秒再隐藏，记得将Y坐标减去10，回到出现前的位置  
        2）当接收到"打到地鼠了"，换成打烂的造型（因为其他地鼠都是隐藏的，所以统一处理即可，不需要再指定具体的克隆体）
![克隆-地鼠2](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_clone_hamster2.jpg)

### 对比一下两种方法下角色的数量（有多少角色就有多少代码）：
复制地鼠地洞：
![第一种方法：复制地鼠和地洞](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_role1.jpg)  

克隆地鼠地洞：
![第二种方法：克隆地鼠和地洞](https://raw.githubusercontent.com/jellier/teachkidscratch/master/thumb/Hamster_role2.jpg)  

是不是使用克隆的方法简洁了很多？ 

## 需要注意的问题：  
>>1. Q: 调整克隆体的位置         
     A: 克隆体每次是在原型当前位置上克隆出新的对象，所以如果想让克隆体出现在合适的位置上，需要先定位XY坐标，再"克隆自己"       
     
     
     
 
