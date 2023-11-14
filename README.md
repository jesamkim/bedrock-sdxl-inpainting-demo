# bedrock-sdxl-inpainting-demo
Amazon Bedrock의 Stable Diffusion XL로 실습하는 이미지 인페인팅 데모 입니다.
---

# Amazon Bedrock 설정


1. AWS 콘솔에서 Amazon Bedrock에 액세스하려는 리전을 선택합니다.

    * 이 글을 쓰는 시점에 Amazon Bedrock은 us-east-1 (버지니아주 북부) 및 us-west-2(오레곤) 리전에서 이용할 수 있습니다. 

![Screenshot of AWS console, selecting region](/img/region-selection.png)




&nbsp;

2. AWS 콘솔에서 검색하여 **Amazon Bedrock** 을 클릭합니다.


![Screenshot of AWS console, searching for Bedrock](/img/bedrock-search.png)



&nbsp;

3. 사이드 메뉴를 펼칩니다.

![Screenshot of Bedrock landing page, showing menu expand link](/img/bedrock-menu-expand.png)


&nbsp;

4. 사이드 메뉴에서 **Model access** 를 선택합니다.

![Screenshot showing Model Access link in menu](/img/model-access-link.png)



&nbsp;

5. **Edit** 버튼을 선택합니다.


![Screenshot of page for available models](/img/model-access-view.png)



&nbsp;

6. 체크박스를 클릭하여 사용하려는 모델을 선택합니다. 필요에 따라 해당하는 최종 사용자 라이센스 계약(EULA)을 검토합니다. **Save changes**을 클릭하여 계정에서 모델을 활성화합니다.

![Screenshot of edit mode for available models](/img/model-access-edit.png)



&nbsp;

7. 모델 액세스 상태를 검토합니다. (Stable Diffusion XL은 반드시 Access granted 여야 합니다.)


![Screenshot of page after models have been selected](/img/model-access-complete.png)

&nbsp;

