#에셋 매니저 익스텐션

이 문서에서는 Cocos2d-JS(JSB만 적용)의 새로운 익스텐션인 에셋 매니저를 소개합니다. 이 익스텐션 이미지, 오디오 파일과 게임 스크립트의 핫업데이트를 위해 설계되었습니다. 게임의 원격 자원을 추적하고 그것들을 디바이스로 다운로드 받을 수 있어서 당신의 웹서버에 새로운 버전의 리소스를 업데이트할 수 있습니다. 전체 새로운 디자인, 새로운 경험이나 새로운 컨텐츠까지도 앱스토어에서의 어플리케이션 업데이트 없이 즉시 업데이트 가능하도록 만들 수 있습니다.

##사용 예

당신의 게임이 이미 앱스토어에 출시되었다고 생각해보세요, 그런데 게임의 어떤 디자인이 만족스럽지 않거나 유저들의 부정적인 의견이 있을 수 있습니다. 일반적으로 당신은 게임을 리패키지하고 앱스토어에 게임을 제출한 후 검증을 통과할 때까지 기다려야 합니다. 이 과정은 매우 고통스럽고 절차가 진행되는 동안 많은 유저들이 떠나가버릴 수 있음을 의미합니다.

다른 예: 

- 성 발렌타인 데이를 위한 게임 활동을 구성하기를 원해서 확실하게 타이밍을 놓치고 싶지 않을 때.
- 밸런스가 완벽하게 붕괴되는 중대한 버그를 찾았을 때.
- 게임 플레이 시간의 확장을 위하여 새로운 레벨이나 씬들의 패키지를 추가하고 싶을 때.
- 그리고 기타 등등

하루 아침에 이 모든 것을 만들 수 있는 기회를 가질 수 있다면 엄청나지 않습니까? 에셋 매니저는 정확하게 이런 목적을 위해 디자인되었습니다.

##기능

Cocos2d-JS v3.0 RC0에서의 에셋 매니저는 아주 편리하고 효율적인 핫 업데이트를 돕기 위한 많은 유용한 기능을 가지고 있습니다.

- 멀티 쓰레드 다운로드 지원
- 두가지 레벨의 진행 지원: 파일 레벨 진행과 바이트 레벨 진행
- Zip 압축 파일 지원
- 다운로드 이어하기
- 세부적인 진행 정보와 에러 정보 
- 실패한 자원에 대한 재시도 가능

##사용

에셋 매니저를 사용하는 것은 꽤 간단합니다. 첫째로 앱 패키지에 JSON 포맷의 초기 메니페스트(manifest) 파일이 필요합니다.

메니페스트 파일에 원격 메니패스트 파일의 온라인 주소, 현재 버전과 리소스 세트를 작성하면 게임이 진행되는 동안 `jsb.AssetsManager` 클래스를 사용해서 업데이트할 수 있습니다.

###메니페스트 파일

여기 JSON 포맷의 메니페스트 파일의 예제가 있습니다:

```
{
	"packageUrl" : "http://example.com/assets_manager/TestScene/",
	"remoteVersionUrl" : "http://example.com/assets_manager/TestScene/version.manifest",
	"remoteManifestUrl" : "http://example.com/assets_manager/TestScene/project.manifest",
	"version" : "1.0.0",
	"engineVersion" : "Cocos2d-JS v3.0 RC0",

	"assets" : {
		"Images/background.jpg" : {
			"md5" : "..."
		},
		"Images/icon.png" : {
			"md5" : "..."
		},
		"Images/button.png" : {
			"md5" : "..."
		},
		"src/game.js" : {
			"md5" : "..."
		},
		"src/layer.js" : {
			"md5" : "..."
		},
		"compressed.zip" : {
			"md5" : "...",
			"compressed" : true
		}
	},
    
    "searchPaths" : [
        "res/"
    ]
}
```

- packageUrl :          모든 자원을 다운로드하고 요청할 수 있도록 하는 에셋 메니저의 URL.
- remoteVersionUrl :    서버에 새로운 버전이 업로드되었는지 여부를 알아내어 원격 버전을 체크할 수 있도록 하는 원격 버전 파일 URL.
- remoteManifestUrl :   모든 자원 정보를 포함하는 원격 메니패스트 파일 URL.
- version :             이 메니페스트 파일의 버전.
- engineVersion :       사용하는 엔진 버전.
- assets :              모든 자원 정보.
    - key : 각각의 키는 자원의 상대적 경로를 나타냅니다.
    - md5 : md5 항목은 자원의 버전 정보를 나타냅니다.
    - compressed : [선택] compressed 항목이 true면 다운로드된 파일은 자동적으로 압축이 풀립니다. 오직 zip 포맷만 지원합니다.
- searchPaths :         cocos2d 엔진에 추가될 검색 경로입니다.

`version.manifest` 파일은 메니페스트 파일의 처음 다섯가지 항목과 정확히 같은 내용이 포함되어야 합니다. 선택적으로 이 파일을 찾을 수 없을 경우 에셋 매니저는 완성된 메니페스트 파일을 직접 다운로드합니다. 그러나 이는 메니페스트 파일이 아주 크기 때문에 버전 정보 비교에 대한 엄청난 시간 절약에 아주 유용할 수 있습니다.

###jsb.AssetsManager의 사용

여기 사용 예제가 있습니다:

```
var manager = new jsb.AssetsManager(manifestUrl, storagePath);

manager.update();
// 프로세스가 비동기적으로 이루어지기 때문에 프로세스가 완료되기 전에 해제하지 않도록 확인하고 에셋 매니저를 유지할 필요가 있습니다.
manager.retain();

if (!manager.getLocalManifest().isLoaded()) {
    cc.log("Fail to update assets, step skipped.");
}
else {
    var listener = new jsb.EventListenerAssetsManager(manager, function(event) {
        switch (event.getEventCode())
        {
            case jsb.EventAssetsManager.ERROR_NO_LOCAL_MANIFEST:
                cc.log("No local manifest file found, skip assets update.");
                break;
            case jsb.EventAssetsManager.UPDATE_PROGRESSION:
                var percent = event.getPercent();
                var filePercent = event.getPercentByFile();
                cc.log("Download percent : " + percent + " | File percent : " + filePercent);
                break;
            case jsb.EventAssetsManager.ERROR_DOWNLOAD_MANIFEST:
            case jsb.EventAssetsManager.ERROR_PARSE_MANIFEST:
                cc.log("Fail to download manifest file, update skipped.");
                break;
            case jsb.EventAssetsManager.ALREADY_UP_TO_DATE:
            case jsb.EventAssetsManager.UPDATE_FINISHED:
                cc.log("Update finished.");
                // 더이상 필요하지 않다면 에셋 매니저를 해제할 필요가 있습니다.
                manager.release();
                break;
            case jsb.EventAssetsManager.UPDATE_FAILED:
                cc.log("Update failed. " + event.getMessage());
                // 이전에 실패한 자원들을 직접 업데이트, 몇번의 재시도 후에 중단하는 것이 좋습니다.
                manager.downloadFailedAssets();
                break;
            case jsb.EventAssetsManager.ERROR_UPDATING:
                cc.log("Asset update error: " + event.getAssetId() + ", " + event.getMessage());
                break;
            case jsb.EventAssetsManager.ERROR_DECOMPRESS:
                cc.log(event.getMessage());
                break;
            default:
                break;
        }
    }
}
```

또한 js-tests 프로젝트의 Extensions/AssetsManagerTest의 테스트 케이스를 참조할 수 있습니다. `jsb.AssetsManager`의 다른 API는 다음고 같습니다:

- checkUpdate()
- getState()
- getStoragePath()
- getLocalManifest()
- getRemoteManifest()

###알려진 문제점

에셋 매니저는 윈도우즈와 iOS 시뮬레이터에서 파일을 생성하고 다운로드하는데 실패할 수 있으나 신속하게 수정할 것입니다. 일단은 실제 iOS 디바이스에서 테스트하세요.
