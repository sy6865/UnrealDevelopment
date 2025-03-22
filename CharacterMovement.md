### 1.移动组件基本原理
移动组件在初始化的时候会把胶囊体设置为移动基础组件UpdateComponent，随后的操作都是在计算UpdateComponent的位置
当然，我们也并不是一定要设置胶囊体为UpdateComponent，对于DefaultPawn会把他的SphereComponent作为UpdateComponent
<br><br><br>

### 2.关系图
#### 2.1继承树
![image](https://github.com/user-attachments/assets/9a53a53b-2149-488a-b092-a654a0749a25)
UPawnMovementComponent组件开始可以和玩家交互, 提供了AddInputVector()接收玩家输入, 玩家通过InputComponent组件绑定一个按键操作，然后在按键响应时调用Pawn的AddMovementInput接口，进而调用移动组件的AddInputVector()，调用结束后会通过ConsumeMovementInputVector()接口消耗掉该次操作的输入数值，完成一次移动操作

最后到了UCharacterMovement, 是基于胶囊体实现的, 所以目前不带胶囊体的Actor是无法正常使用的
<br><br>

#### 2.2移动框架相关类图
![image](https://github.com/user-attachments/assets/e7446d05-1e51-497e-8c85-b6e9ba4eae76)
<br><br><br>

### 3.各个状态细节处理
#### 3.1Walking
