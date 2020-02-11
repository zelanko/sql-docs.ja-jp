---
title: sysssispackages (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdtspackages90_TSQL
- sysdtspackages90
dev_langs:
- TSQL
helpviewer_keywords:
- sysssispackages system table
ms.assetid: 66155dcd-dcdb-4e33-a242-1625828ad8d2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 21487ba46e53997ebb50403cc4eaf1ae54f0a103
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029643"
---
# <a name="sysssispackages-transact-sql"></a>sysssispackages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  に保存されているパッケージごとに 1 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]行の値を格納します。 このテーブルは、 **msdb**データベースに格納されます。  
  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|パッケージの一意識別子です。|  
|**番号**|**UNIQUEIDENTIFIER**|パッケージの GUID。|  
|**記述**|**nvarchar**|パッケージの説明 (省略可)。|  
|**createdate**|**DATETIME**|パッケージが作成された日付。|  
|**folderid**|**UNIQUEIDENTIFIER**|
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] によってパッケージの一覧が格納される論理フォルダーの GUID。|  
|**ownersid**|**varbinary**|パッケージを作成したユーザーの一意のセキュリティ識別子。|  
|**(microsoft.sql.chainer.packagedata.dll**|**絵**|パッケージです。|  
|**packageformat**|**int**|パッケージが保存される形式は次のとおりです。<br /><br /> 値が2の場合は、パッケージが[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]形式で保存されていることを示します。<br /><br /> 値3は、パッケージが以降の[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]形式で保存されることを示します。|  
|**packagetype**|**int**|パッケージを作成したクライアント。 次のような値が考えられます。<br /><br /> 0 (既定値)<br /><br /> 1 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インポートおよびエクスポートウィザード)<br /><br /> 3 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション)<br /><br /> 5 ([!INCLUDE[ssIS](../../includes/ssis-md.md)]デザイナー)<br /><br /> 6 (メンテナンス プラン デザイナーまたはメンテナンス プラン ウィザード)<br /><br /> <br /><br /> この列の値は<xref:Microsoft.SqlServer.Dts.Runtime.DTSPackageType>列挙型に対応していることに注意してください。|  
|**vermajor**|**int**|パッケージの最新のメジャー バージョン。|  
|**verminor**|**int**|パッケージの最新のマイナー バージョン。|  
|**verbuild**|**int**|パッケージの最新のビルドです。|  
|**vercomments**|**nvarchar**|パッケージ バージョンについてのコメント。|  
|**verid**|**UNIQUEIDENTIFIER**|パッケージのバージョンの GUID。|  
|**isencrypted**|**bit**|パッケージが暗号化されているかどうかを示すブール値です。|  
|**readロール id**|**varbinary**|パッケージ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を読み込むことができるロール。|  
|**writerolesid**|**varbinary**|パッケージ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を保存できるロール。|  
  
## <a name="see-also"></a>参照  
 [SSIS&#41; パッケージ &#40;Integration Services](../../integration-services/integration-services-ssis-packages.md)  
  
  
