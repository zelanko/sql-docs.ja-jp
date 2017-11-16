---
title: "Update-powerpivotsystemservice コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a90f1158-68d3-4330-98c1-fb0f81e13328
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4ac64af222158746d63530f236eeda8cb94f2260
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="update-powerpivotsystemservice-cmdlet"></a>Update-PowerPivotSystemService コマンドレット

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  親オブジェクトをアップグレード、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のシステム サービスです。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## <a name="syntax"></a>構文  
  
```  
Update-PowerPivotSystemService [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 **Update-PowerPivotSystemService** コマンドレットでは、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] システム サービスの親オブジェクト、インスタンス、および [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションに対して一連のアップグレード アクションを実行します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint の展開のすべての中間層サービスとアプリケーションは、同じ機能レベルで実行する必要があります。 このコマンドレットは、これらのすべてのオブジェクトのアップグレード アクションを実行します。  
  
 新しいバージョンをインストールする SQL Server セットアップを実行した後に、このコマンドレットを実行 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint またはサーバーに累積更新プログラムを適用してあるかどうか。 アップグレードが必要かどうかを確認するには、 `Get-PowerPivotSystemService` を実行して **NeedsUpgrade** プロパティを確認します。 **NeedsUpgrade** が true の場合は、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 中間層オブジェクトをアップグレードするために、このコマンドレットを実行する必要があります。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint の配置には中間層およびバックエンド データ サービスが含まれるため、ファーム間でどちらの層も同じバージョンとなるように、 **Update-PowerPivotSystemService** を実行するたびに **Update-PowerPivotEngineService** を実行する必要があります。  
  
 以前のバージョンにアップグレードをロールバックすることはできません。 以前のバージョンに戻す、削除 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、SharePoint からファームし、ソフトウェアを再インストールします。 アップグレード操作が成功したことを検証するには、 `Get-PowerPivotSystemService` を実行してバージョン情報のグローバル プロパティを確認し、 **NeedsUpgrade** が true ではなくなっていることを確認します。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-confirm-switch"></a>確認\<スイッチ >  
 コマンドを実行する前に確認メッセージを表示します。 既定では、この値は有効にされています。 コマンドで確認応答を省略するには、コマンドで Confirm:$false を指定してください。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 このコマンドレットは、次のパラメーターをサポートしています。  
  
-   [詳細]  
  
-   デバッグ  
  
-   ErrorAction  
  
-   ErrorVariable  
  
-   WarningAction  
  
-   WarningVariable  
  
-   OutBuffer  
  
-   OutVariable  
  
 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|[なし] :|  
  
  

