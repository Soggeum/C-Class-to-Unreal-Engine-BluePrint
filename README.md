# C-Class-to-Unreal-Engine-BluePrint
basic practice for Unreal Engine Implementation

# Purpose
- 간단한 기능을 가진 액터클래스를 C++로 만들어 본 후, 언리얼 엔진에 블루프린터로 상속시켜보는 실습

# MyActor

- 10번 랜덤하게 이동하면서, 이동한 위치와 이동한 거리를 출력
- 각 이동마다 50% 확률의 이벤트 발생
- 10번의 이동이 완료된 후, 이동한 거리와 이벤트 발생횟수를 로그로 출력
  
  <img width="363" height="297" alt="image" src="https://github.com/user-attachments/assets/1b5813a4-16fd-43fc-82da-2f65e7d3ae56" />

# UHT

- 언리얼 엔진에서 우리가 만든 C++ 클래스를 사용하려면 그에 맞게 UObject로 만들어줘야함
- 그 과정에서 필요한 것이 UHT 코드
```cpp
UCLASS()  // UHT
class ASSIGNMENT5_API AMyActor : public AActor
{
	GENERATED_BODY()  // UHT
	
public:	
	UFUNCTION(BlueprintCallable, Category = "Actions")  // UHT
	void move();

	float distance(FVector2D first, FVector2D second);

  UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "MyVariables")  // UHT
  int32 a;

private:
	FVector2D start;
```
- 먼저 UHT 코드를 넣어 해당 클래스가 Unreal Engine에서도 사용할 수 있게 설정해주고
- `UFUNCTION`, `UPROPERTY`를 통해서도 해당 함수, 변수가 에디터에서 어떻게 쓰일 것인지를 설정해준다
- 에디터에서 사용하려면 무조건 public으로 선언해야함
- 따라서 `move()`, `a`만 에디터에서 나타나며 사용할 수 있다
