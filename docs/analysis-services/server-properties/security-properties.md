---
title: "セキュリティのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- security [Analysis Services], properties
- SecurityPackageList property
- BuiltinAdminsAreServerAdmins property
- DisableClientImpersonation property
- ErrorMessageMode property
- RequiredProtectionLevel property
- ServiceAccountIsServerAdmin property
- RequireClientAuthentication property
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
caps.latest.revision: 15
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0233cd9c2e9eff5cc776b921e092206524546a52
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="security-properties"></a>セキュリティのプロパティ
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 次の表に示すセキュリティ サーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードおよびテーブル サーバー モード  
  
## <a name="properties"></a>プロパティ  
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
  
  

