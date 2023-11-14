# Amazon Bedrock - Stable Diffusion XL 이미지 인페인팅 DEMO

---

앱은 Streamlit으로 구동되며 아래와 같습니다.<br><br>
![Demo capture](/img/demo-capture1.png) <br><br>
왼쪽 이미지에서 마우스로 드래그 하면서 선을 여러 번 그려서 마스크 영역을 지정합니다.<br>
이미지 프롬프트에 "2pac printing" 과 같은 프롬프트를 입력하고, 오른쪽의 <b>생성하기</b> 버튼을 클릭 합니다.<br>
(마스크 영역을 다르게 하거나, SDXL의 파라미터 값을 조정하면서 테스트 해보세요.)<br>

---

## 1. Amazon Bedrock 설정

#### 1-1. AWS 콘솔에서 Amazon Bedrock에 액세스하려는 리전을 선택합니다.

- 이 글을 쓰는 시점에 Amazon Bedrock은 us-east-1 (버지니아주 북부) 및 us-west-2(오레곤) 리전에서 이용할 수 있습니다.


![Screenshot of AWS console, selecting region](/img/bedrock-setup/region-selection.png)




&nbsp;

#### 1-2. AWS 콘솔에서 검색하여 **Amazon Bedrock** 을 클릭합니다.


![Screenshot of AWS console, searching for Bedrock](/img/bedrock-setup/bedrock-search.png)



&nbsp;

1-3. 사이드 메뉴를 펼칩니다.

![Screenshot of Bedrock landing page, showing menu expand link](/img/bedrock-setup/bedrock-menu-expand.png)


&nbsp;

#### 1-4. 사이드 메뉴에서 **Model access** 를 선택합니다.

![Screenshot showing Model Access link in menu](/img/bedrock-setup/model-access-link.png)



&nbsp;

#### 1-5. **Edit** 버튼을 선택합니다.


![Screenshot of page for available models](/img/bedrock-setup/model-access-view.png)



&nbsp;

#### 1-6. 체크박스를 클릭하여 사용하려는 모델을 선택합니다. 필요에 따라 해당하는 최종 사용자 라이센스 계약(EULA)을 검토합니다. **Save changes**을 클릭하여 계정에서 모델을 활성화합니다.

![Screenshot of edit mode for available models](/img/bedrock-setup/model-access-edit.png)



&nbsp;

#### 1-7. 모델 액세스 상태를 검토합니다. (Stable Diffusion XL은 반드시 Access granted 여야 합니다.)


![Screenshot of page after models have been selected](/img/bedrock-setup/model-access-complete.png)

&nbsp;



---

&nbsp;



## 2. AWS Cloud9 설정



#### 2-1. AWS 콘솔에서 Amazon Bedrock 파운데이션 모델이 활성화된 지역을 선택합니다.


![AWS Console region selection](/img/cloud9-setup/region-selection.png)

&nbsp;


#### 2-2. AWS 콘솔에서 **Cloud9**를 검색합니다.

    * 검색 결과에서 **Cloud9**를 선택합니다.

![Search results for AWS Cloud9](/img/cloud9-setup/search-cloud9.png)

&nbsp;


#### 2-3. **Create environment**을 클릭합니다.

![AWS Cloud9 welcome page](/img/cloud9-setup/cloud9-welcome.png)

&nbsp;


#### 2-4. 환경 세부 정보를 설정합니다.

	* **Name** 을 :code[bedrock-environment]{showCopyAction=true} 로 설정합니다.



![Environment details editor panel](/img/cloud9-setup/environment-details.png)

&nbsp;

#### 2-5.  EC2 인스턴스 세부 정보를 설정합니다.-
- **인스턴스 유형**을 **t3.small**로 설정합니다.
- **플랫폼**을 **Ubuntu Server 22.04 LTS**로 설정합니다.
- **시간 제한**을 4시간으로 설정합니다.

![New EC2 instance editor panel](/img/cloud9-setup/cloud9-ubuntu-instance.png)


&nbsp;

#### 2-6. **Create** 버튼을 선택합니다.

![Create button screenshot](/img/cloud9-setup/create-button.png)

&nbsp;

#### 2-7. 환경이 생성될 때까지 기다립니다.

- 준비가 완료되면 상단 배너에 "Successfully created bedrock-environment."라는 메시지가 표시됩니다.
- 환경 목록에서 **Open** 링크를 클릭합니다. 그러면 새 탭에서 AWS Cloud9 IDE가 시작됩니다.

* 만약 선택한 인스턴스 유형을 가용 영역에서 사용할 수 없다는 오류 메시지가 표시되면 환경을 삭제하세요. 다른 크기의 인스턴스 유형으로 프로비저닝을 다시 시도하세요.




![AWS Cloud9 screen with success banner](/img/cloud9-setup/cloud9-ready.png)

&nbsp;

#### 2-8. AWS Cloud9 환경이 제대로 로드되었는지 확인합니다.
- **Welcome** 탭을 닫을 수 있습니다.
- 탭을 원하는 위치로 드래그할 수 있습니다.

![Cloud9 IDE loaded](/img/cloud9-setup/cloud9-ide.png)

&nbsp;

이 예제에서는 bash 터미널 탭을 위쪽 탭 스트립으로 드래그하고 아래쪽에 정렬된 패널을 닫았습니다:

![Cloud9 IDE layout customized](/img/cloud9-setup/cloud9-panels.png)

&nbsp;

---

## 3. AWS Cloud9 에서 코드 실행

#### 3-1. Cloud9 터미널에서 아래 커맨드를 실행합니다.
```
git clone https://github.com/jesamkim/bedrock-sdxl-inpainting-demo.git

```

#### 3-2. 이어서 코드 실행에 필요한 디펜던시를 설치 합니다.
```
pip install -r ../dependencies/requirements.txt --quiet
```

#### 3-3. 이어서 스트림릿을 구동 합니다.
```
cd bedrock-sdxl-inpainting-demo/source_code

streamlit run mask_image_app.py --server.port 8501
```

#### 3-4. AWS Cloud9에서 **Preview** -> **Preview Running Application**을 선택합니다.
![Screenshot of terminal, showing the Cloud9 preview button](/img/cloud9-setup/cloud9-preview.png)
