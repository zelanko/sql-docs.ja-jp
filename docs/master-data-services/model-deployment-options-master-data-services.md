---
title: "モデル配置オプション (マスター データ サービス) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf1b17b4-47d5-4eba-83f9-fb0555806867
caps.latest.revision: 6
author: smartysanthosh
ms.author: nagavo
manager: craigg
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: 0b832a9306244210e693bde7c476269455e9b6d8
ms.openlocfilehash: 6e4cdd4041ee2065b6cd2aa898068289eda66d9e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="model-deployment-options-master-data-services"></a>モデル配置オプション (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデル パッケージ ファイルを配置するとき、新しいモデルまたは複製モデルを配置するのか、以前に複製したモデルを更新するのかを決定する必要があります。  
  
## <a name="workflows"></a>ワークフロー  
 モデル パッケージを操作する場合、2 つの主要なワークフローがあります。  
  
-   テスト環境でモデルのパッケージを作成し、そのモデルの複製を運用環境に配置します。 後で、テスト環境から運用環境に更新を配置します。  
  
-   モデルのパッケージを作成し、同じ環境に新しいモデルとして配置します。 この場合、モデルに新しい名前を付ける必要があります。  
  
## <a name="options"></a>オプション  
 MDS データベースでは、各モデル オブジェクトに一意の識別子 (ID) があります。 これらの ID は、モデルの配置パッケージに含まれます。 パッケージを配置する際、これらの ID をどのように処理するかを選択する必要があります。  
  
 次の表は、システム管理のモデル配置ウィザードまたは MDSModelDeploy ツールのいずれかを使用してモデルを配置する際に何を選択すればよいかを決定するのに役立ちます。  
  
|オプション|Description|注|  
|------------|-----------------|-----------|  
|新規|一意の名前を持つ新しいモデルを作成します。 すべてのモデル オブジェクトに新しい識別子が作成されます。|新しい識別子を持つ新しいモデルを作成した場合、後でモデル配置ツールを使用してモデルに更新を適用することはできません。 Web アプリケーションのウィザードを使用してモデル パッケージを配置ときに、同じ名前または ID を持つモデルが既に存在している場合、選択できるのは新しいモデルの作成のみです。|  
|複製|パッケージ内のモデルの正確な複製である新しいモデルを作成します。 このオプションは、名前または識別子が同じモデルがターゲット環境内に存在しない場合にのみ機能します。 複数の環境に同じモデルがあり、複製したモデルを後で更新する場合は、"複製" を使用します。|これは、Web アプリケーションのウィザードの既定の動作です。 同じ名前または ID を持つモデルが既に存在する場合は、代わりに新しいモデルを作成するよう求められます。|  
|Update|パッケージ内のモデルを使用して、既存のモデルを更新します。 両方のモデルの識別子が同じである必要があります。 このオプションは、以前に複製したモデルを更新するために使用します。|以前に複製したモデルのみを更新できます (名前と ID が一致する必要があります)。|  
  
## <a name="see-also"></a>参照  
 [MDSModelDeploy を使用したモデルの配置パッケージの配置](../master-data-services/deploy-a-model-deployment-package-by-using-mdsmodeldeploy.md)   
 [ウィザードを使用したモデルの配置パッケージの展開](../master-data-services/deploy-a-model-deployment-package-by-using-the-wizard.md)   
 [モデルの配置 (マスター データ サービス)](../master-data-services/deploying-models-master-data-services.md)  
  
  

