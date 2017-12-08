---
title: "New-powerpivotserviceapplication コマンドレット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: powershell
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7bb2a2d2-04c8-43d4-a0fc-e8339ea22138
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ec99b8511d512c068130ed7bc521f447b57d20d9
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="new-powerpivotserviceapplication-cmdlet"></a>New-PowerPivotServiceApplication コマンドレット

[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

  新たに作成 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーション。  

>[!NOTE] 
>この記事には、古くなった情報と例があります。 最新バージョンには、Get-help コマンドレットを使用します。
  
 **適用対象:** SharePoint 2010 および SharePoint 2013  
  
## <a name="syntax"></a>構文  
  
```  
New-PowerPivotServiceApplication [-ServiceApplicationName] <string> [-DatabaseServerName] <string> [-DatabaseName] <string> [-AddToDefaultProxyGroup <switch>] [<CommonParameters>]  
```  
  
## <a name="description"></a>Description  
 New-PowerPivotServiceApplication コマンドレットは、ファームで新しい [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションを作成します。 少なくとも 1 つのサービス アプリケーションを定義し、それは既定のプロキシ サービス グループのメンバーである必要があります。 必要に応じて、プロパティまたは構成の設定を変更する必要がある場合は、追加のサービス アプリケーションを作成できます。 追加のサービス アプリケーションは、カスタム サービス接続グループにメンバーシップを割り当てる必要があります。 1 つだけ [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションは既定のプロキシ グループのメンバーであることができます。  
  
 新しいサービス アプリケーションは、既定の構成を使用して作成されます。 構成プロパティをカスタマイズするには、Set-PowerPivotServiceApplication コマンドレットを使用します。  
  
## <a name="parameters"></a>パラメーター  
  
### <a name="-serviceapplicationname-string"></a>-Serviceapplicationname &\<文字列 >  
 サービス アプリケーションの表示名を設定します。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|0|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-databaseservername-string"></a>-Databaseservername &\<文字列 >  
 アプリケーション データベースをホストする SQL Server リレーショナル データベース エンジン インスタンスを指定します。 既定では、ファームのデータベース サーバーを使用するか、データベース権限を作成する他のデータベース サーバーを選択できます。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|1|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-databasename-string"></a>-DatabaseName\<文字列 >  
 アプリケーション データを格納する SQL Server リレーショナル データベースの名前を指定します。 目的を簡単に識別できるように、アプリケーションに対応した名前を指定する必要があります。 新しいデータベースを作成したり、既存の指定 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] を作成する新しいアプリケーションのサービス アプリケーション データベース。  
  
|||  
|-|-|  
|必須/省略可能|true|  
|位置|2|  
|既定値||  
|パイプライン入力の受け入れ|オプション|  
|ワイルドカード文字の受け入れ|オプション|  
  
### <a name="-addtodefaultproxygroup-switch"></a>-Addtodefaultproxygroup &\<スイッチ >  
 作成、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 既定のサービス接続グループ内の接続にサービスを提供します。 Web アプリケーションとサービス アプリケーション間の関連付けは、このグループのメンバーシップによって決定されます。 既定のサービス接続グループにサブスクライブするすべての web アプリケーションを使用して、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス、グループに追加するアプリケーション。 複数を設定できますが、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ファームでは、アプリケーションをサービスだけで 1 つのサービス アプリケーションは既定のサービス接続グループのメンバーであることができます。  
  
 既にある場合 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 既定のプロキシ グループのメンバーであるサービス アプリケーションで AddToDefautlProxyGroup を設定する必要があります: $false を作成する新しいアプリケーションにします。 新しいサービス アプリケーションを、カスタム サービス接続グループに追加する必要があります。  このために、組み込みの SharePoint コマンドレットを使用することができます。  Get-SPServiceApplicationProxyGroup は、ファームで定義されているサービス接続グループの一覧を返します。  
  
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
C:\PS>New-PowerPivotServiceApplication -ServiceApplicationName "PowerPivot Service Application" -DatabaseServerName "AdvWorks-SRV01\PowerPivot" -DatabaseName "PowerPivotServiceApp1" -AddtoDefaultProxyGroup:$true  
```  
  
 この例では、新しいサービス アプリケーションを作成します。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 名前付きインスタンスとしてインストールされた AdvWorks-SRV01 という名前のデータベース サーバーでサービス アプリケーション データベースが作成されます。多くの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint インストールの共通の構成です。 データベースを作成するには、SQL Server インスタンス上で dbcreator 権限が必要です。 SharePoint 構成データベースで db_owner である必要があります。 これは、1 つあるため [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サービス アプリケーションに、ファームの既定のプロキシ グループのメンバーである必要があります。  
  
  
