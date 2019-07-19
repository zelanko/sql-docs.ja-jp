---
title: Analysis Services のセキュリティのプロパティ |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 31191e266b017400b8b8aceb2eb912f9bebca3d5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68163480"
---
# <a name="security-properties"></a>セキュリティ プロパティ
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 次の表に示すセキュリティ サーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元および表形式サーバー モード  
  
## <a name="properties"></a>Properties  
 **RequireClientAuthentication**  
 クライアント認証が必要かどうかを示すブール型プロパティです。  
  
 このプロパティの既定値は True で、クライアント認証が必要であることを示します。  
  
 **SecurityPackageList**  
 サーバーがクライアントの認証に使用する SSPI パッケージのコンマ区切りのリストを格納する文字列プロパティです。  
  
 **DisableClientImpersonation**  
 (たとえばストアド プロシージャからの) クライアント権限の借用が無効であるかどうかを示すブール型プロパティです。  
  
 このプロパティの既定値は False で、クライアント権限の借用が有効であることを示します。  
  
 **BuiltinAdminsAreServerAdmins**  
 ローカル コンピューターの Administrators グループのメンバーが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理者であるかどうかを示すブール型プロパティです。  
  
 **ServiceAccountIsServerAdmin**  
 サービス アカウントがサーバー管理者であるかどうかを示すブール型プロパティです。  
  
 このプロパティの既定値は True で、サービス アカウントがサーバー管理者であることを示します。  
  
 **ErrorMessageMode**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **DataProtection\ RequiredProtectionLevel**  
 すべてのクライアント要求に必要な保護レベルを定義する、符号付き 32 ビット整数のプロパティです。 このプロパティは、次の表に示すいずれかの値になります。  
  
|値|説明|  
|-----------|-----------------|  
|*0*|なし。クリア テキストが許可されます。|  
|*1*|(既定値) 暗号化が必要。クリア テキストのログは記録されません。|  
|*2*|クリア テキストの要求は許可されるが、署名付きのものに限る (暗号化より弱い保護)。|  
  
 **AdministrativeDataProtection\ RequiredProtectionLevel**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
