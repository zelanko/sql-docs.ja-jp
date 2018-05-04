---
title: sysssispackages (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
caps.latest.revision: 43
author: douglasl
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1143dc7897d5725279c2146d295bb5146fcc628c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  保存されているパッケージごとに 1 つの行を含む[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 次の表は、 **msdb**データベース。  
  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|パッケージの一意識別子です。|  
|**id**|**uniqueidentifier**|パッケージの GUID。|  
|**説明**|**nvarchar**|パッケージの説明 (省略可)。|  
|**createdate**|**datetime**|パッケージが作成された日付。|  
|**folderid**|**uniqueidentifier**|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] によってパッケージの一覧が格納される論理フォルダーの GUID。|  
|**ownersid**|**varbinary**|パッケージを作成したユーザーの一意なセキュリティ識別子。|  
|**packagedata**|**image**|パッケージです。|  
|**packageformat**|**int**|パッケージの保存形式。<br /><br /> 2 の値でパッケージを保存することを示す、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]形式です。<br /><br /> 値 3 がの形式でパッケージを保存することを示す[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]またはそれ以降。|  
|**packagetype**|**int**|パッケージを作成したクライアント。 次のような値が考えられます。<br /><br /> 0 (既定値)<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポート ウィザード)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナー)<br /><br /> 6 (メンテナンス プラン デザイナーまたはメンテナンス プラン ウィザード)<br /><br /> <br /><br /> この列の値に対応している、<xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType>列挙します。|  
|**vermajor**|**int**|パッケージの最新のメジャー バージョン。|  
|**verminor**|**int**|パッケージの最新のマイナー バージョン。|  
|**verbuild**|**int**|パッケージの最新のビルド。|  
|**vercomments**|**nvarchar**|パッケージ バージョンについてのコメント。|  
|**verid**|**uniqueidentifier**|パッケージ バージョンの GUID。|  
|**isencrypted**|**bit**|パッケージが暗号化されているかどうかを示すブール値。|  
|**readrolesid**|**varbinary**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パッケージを読み込むことができるロール。|  
|**writerolesid**|**varbinary**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パッケージを保存することができるロール。|  
  
## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS & #41;パッケージ](../../integration-services/integration-services-ssis-packages.md)  
  
  
