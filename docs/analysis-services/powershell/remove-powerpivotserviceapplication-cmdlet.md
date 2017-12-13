---
title: "Remove-powerpivotserviceapplication コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 2742b2a3-927c-4e7c-bd7d-43c072fa01ab
caps.latest.revision: "11"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 7cf2627ebb14d37ea684adc76cd0d8a5d003d73c
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="remove-powerpivotserviceapplication-cmdlet"></a>Remove-PowerPivotServiceApplication コマンドレット
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]削除、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]サービス アプリケーション。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## <a name="syntax"></a>構文  
  
```  
Remove-PowerPivotServiceApplication [-Identity <SPGeminiServiceApplicationPipeBind>] [-DeleteAll <switch>] [-RemoveData <switch>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 Remove-powerpivotserviceapplication コマンドレットを削除、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ファームからのアプリケーションのサービスを提供します。 DeleteAll を使用してすべてのサービス アプリケーションを一度に削除するか、Identity パラメーターを使用して 1 つのインスタンスを削除します。 インスタンス情報を取得するには、ファーム内のすべてのインスタンスを返す Get-PowerPivotServiceApplication を実行します。  
  
 必要に応じて、RemoveData パラメーターを使用して、サービス アプリケーション データベースとキャッシュされたファイルを削除します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックでは、コンテンツ ライブラリに残りますが、サービス アプリケーションが削除されると、機能が不要になった。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-identity-spgeminiserviceapplicationpipebind"></a>Id \<SPGeminiServiceApplicationPipeBind >  
 1 つの GUID を指定 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のアプリケーションのサービスを提供します。 他のサービス アプリケーションをそのまま残してアプリケーションを 1 つだけ削除する場合、GUID を指定する必要があります。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|true|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-confirm-switch"></a>確認\<スイッチ >  
 コマンドを実行する前に確認メッセージを表示します。 既定では、この値は有効にされています。 コマンドで確認応答を省略するには、コマンドで Confirm:$false を指定してください。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-deleteall-switch"></a>-Deleteall\<スイッチ >  
 すべて削除 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービスのアプリケーションは、ファーム内のサービス アプリケーション データベースおよびサービス インスタンスのオブジェクトを削除します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] System サービスと [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] エンジン サービス オブジェクトは残りますが、インスタンス化された、使用できない場合は、サービス アプリケーションを削除した後です。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-removedata-switch"></a>-Removedata &\<スイッチ >  
 データ更新スケジュール、ブック使用状況データ、データベースが読み込まれるトラックで使用されるインスタンス マップ、その他の内部データを含むサービス アプリケーション データベースを削除します。  
  
|||  
|-|-|  
|必須/省略可能|オプション|  
|位置|指定|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="commonparameters"></a>\<CommonParameters >  
 このコマンドレットは共通のパラメーターをサポートしています (Verbose、Debug、ErrorAction、ErrorVariable、WarningAction、WarningVariable、OutBuffer、および OutVariable)。 詳細については、「 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)」を参照してください。  
  
## <a name="inputs-and-outputs"></a>入力および出力  
 入力型は、コマンドレットにパイプできるオブジェクトの型です。 戻り値の型は、コマンドレットが返すオブジェクトの型です。  
  
|||  
|-|-|  
|入力|[なし] :|  
|出力|[なし] :|  
  
## <a name="example-1"></a>例 1  
  
```  
C:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop  
```  
  
 次の例は、1 つを削除 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションしますが、データベースまたはキャッシュは削除されません。 ID を指定しないと、指定するように促されます。  
  
## <a name="example-2"></a>例 2  
  
```  
C:\PS>Remove-PowerPivotServiceApplication -DeleteAll  
```  
  
 この例では、すべてを削除 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 、ファーム内のアプリケーションのサービスを提供します。 データベースとキャッシュは削除されません。  
  
## <a name="example-3"></a>例 3  
  
```  
CC:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop -RemoveData  
```  
  
 次の例は、1 つを削除 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションと、そのデータベースおよびキャッシュ ファイルです。  
  
  
