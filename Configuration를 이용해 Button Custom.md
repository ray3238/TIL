> # Button.***\*Configuration를 이용해 Button Custom\****
>
> ------
>
> > **UIButton.Configuration**
>
> - iOS 15.0부터 이용 가능
> - Struct 타입
>
> 기본적으로 제공하는 Configuration 메서드의 형태가 존재
>
> ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3a43468a-0f71-4f8b-87a5-c4d40798ae72/77703244-7b5d-4087-92ce-8cd523e11827/Untitled.png)
>
> 주로 사용되는건 이정도이다.
>
> - UIButton.Configuration.**plain()**
> - UIButton.Configuration.**tinted()**
> - UIButton.Configuration.**gray()**
> - UIButton.Configuration.**filed()**
>
> ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3a43468a-0f71-4f8b-87a5-c4d40798ae72/600e124e-a891-4494-8247-81394cc402c8/Untitled.png)
>
> Configuration의 여러 프로퍼티를 수정해서 타이틀, 배경색, 테두리, 이미지, 동작 등을 많은 요소들을 커스텀할 수 있다.
>
> Configuration을 적용한 상태에서 titleLabel의 font를 수정할 경우 아무 변화도 일어나지 않는데, 그 이유는 UIButton 내부에는 Configuration외에 버튼 설정을 도와주는 여러 메소드와 프로퍼티들이 존재하기 때문이라고 한다.
>
> Configuration에는 주로 3가지 프로퍼티가 있는데 각각
>
> - **Contents**
> - **Appearance**
> - **Behavior**
>
> 이다.
>
> ## Contents
>
> Contents 그룹 내에서는 title, subtitle, image 프로퍼티를 주로 사용한다.
>
> 이름에서도 유추할 수 있듯이 버튼 내부에 들어가는 내용들을 커스텀할 수 있다.
>
> ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3a43468a-0f71-4f8b-87a5-c4d40798ae72/c373fd9f-9161-430e-ac3d-93c801ba1fbc/Untitled.png)
>
> 글자색 또는 폰트를 변경하고 싶으면 attributedTitle과 attributedSubtitle 프로퍼티를 사용.
>
> 이미지의 위치뿐 만 아니라 텍스트의 정렬 방향, 타이틀과 이미지 사이의 padding 또는 버튼과 내부 content 영역 사이의 inset을 설정할 수도 있다.
>
> ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3a43468a-0f71-4f8b-87a5-c4d40798ae72/ae794d9a-62f3-4a84-bc4d-e1210a49dcb9/Untitled.png)
>
> ```swift
> // 위 버튼을 커스텀한 코드
> q
> var configuration = UIButton.Configuration.filled()
>         
> var titleContainer = AttributeContainer() 
> titleContainer.font = UIFont.boldSystemFont(ofSize: 20)
> 
> var subtitleContainer = AttributeContainer()
> subtitleContainer.foregroundColor = UIColor.white.withAlphaComponent(0.5)
> 
> // 버튼 Contents 커스텀
> configuration.attributedTitle = AttributedString("Title", attributes: titleContainer) 
> configuration.attributedSubtitle = AttributedString("Subtitle", attributes: subtitleContainer)
> configuration.image = UIImage(systemName: "swift")
> configuration.preferredSymbolConfigurationForImage = UIImage.SymbolConfiguration(pointSize: 30) 
> configuration.imagePadding = 10
> 
> // 이미지가 왼쪽에 위치한 버튼
> configuration.titleAlignment = .leading
> let leftButton = UIButton(configuration: configuration)
> 
> // 이미지가 상단에 위치한 버튼
> configuration.imagePlacement = .top
> let topButton = UIButton(configuration: configuration)
> 
> // 이미지가 오른쪽에 위치한 버튼
> configuration.imagePlacement = .trailing
> let rightButton = UIButton(configuration: configuration)
> 
> // 이미지가 하단에 위치한 버튼
> configuration.imagePlacement = .bottom
> let bottomButton = UIButton(configuration: configuration)
> ```
>
> ## Appearance
>
> 버튼의 색, 크기, 배경, 테두리 등 버튼의 외관을 결정하는 값을 커스텀
>
> > 주로 사용하는 프로퍼티
>
> - buttonSize
> - background
> - cornerStyle
>
> buttonSize와 cornetStyle에 따른 버튼의 형태
>
> ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3a43468a-0f71-4f8b-87a5-c4d40798ae72/66f6752a-d330-4454-a43b-029ddf97ee9f/Untitled.png)
>
> ```
>                         **buttonSize**
> ```
>
> ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/3a43468a-0f71-4f8b-87a5-c4d40798ae72/2cc344e9-2b5a-4db0-9cc7-2d58b8a585b6/Untitled.png)
>
> ```
>                         **cornerStyle**
> ```
>
> > **CornerStyle**
>
> - fix
>   - 둥근 모서리를 그릴때 버튼의 configuration.background.cornerRadius 프로퍼티에 저장된 고정값을 사용하는 설정
> - dynamic
>   - 기기에 설정된 텍스트 크기값에 따라 cornerRadius 값을 동적으로 변하게 만드는 설정
>
> **※ 설정한 buttonSize는 내부 Contents의 설정값에 따라 재정의될 수 있다.**
>
> 즉, 버튼의 크기를 작게 설정했더라도 버튼의 이미지와 타이틀 크기에 따라 변경될 수 있다.
>
> > **Background**
>
> UIBackgroundConfiguration 타입으로 버튼의 배경을 커스텀할 때 사용
>
> 내부의 대표 프로퍼티로는
>
> - cornerRadius: 버튼의 모서리가 둥근 정도
> - backgroundColor: 배경색
> - strokeColor: 테두리 색
> - strokeWidth: 테두리 굵기
>
> 등등이 존재
>
> ### **backgroundColor와 baseBackgroundColor의 차이점**
>
> baseBackgroundColor에 설정된 색상이 그대로 버튼의 배경색에 적용되는 것은 아님 그 예시로 plain과 tinted로 설정된 버튼에 해당 프로퍼티의 색을 변경할 경우 plain은 투명한 배경을, tinted는 설정한 색이 투명하게 보인다. 즉, base는 말 그대로 base다. 이 프로퍼티에 설정한 색이 버튼에 적용되기 전에 변형될 수 있다~
>
> > **Behavior**
>
> 버튼의 상태에 따른 행동을 커스텀할 수 있다.
>
> 예) 버튼을 눌렀을 때 배경색이 바뀜 → ConfigurationUpdateHandler를 사용
>
> ```swift
> // 버튼을 눌렀을 때 배경색이 바뀌도록 만든 코드
> button.configurationUpdateHandler = { button in
>             
>             var container = AttributeContainer()
>             container.font = .systemFont(ofSize: 20, weight: .bold)
>             
>             var configuration = button.configuration
>             
>             switch button.state {
>                 
>             case .selected:
>                 container.foregroundColor = .white
>                 configuration?.background.backgroundColor = .systemBlue
>                 configuration?.attributedTitle = AttributedString("준비 완료!", attributes: container)
>             case .highlighted:
>                 break
>             default:
>                 container.foregroundColor = .black
>                 configuration?.background.backgroundColor = .systemGray6
>                 configuration?.attributedTitle = AttributedString("준비", attributes: container)
>             }
>             
>             button.configuration = configuration
>             
>         }
> ```
>
> 버튼을 누르면 isSelected가 true가 되어 selected 상태로 만들고 위 클로저를 호출하여 내부에서 버튼의 배경색과 타이틀을 변경한다.
>
> 버튼을 다시 한번 누르면 isSelected가 false가 되고 버튼의 상태가 normal이 되어 원래 설정값을 갖도록 한다.