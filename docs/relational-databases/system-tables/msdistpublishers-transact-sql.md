---
title: MSdistpublishers (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 26b26690d1120ce66dd116ed7908a68fe594e077
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85753931"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]
  **Msdistpublishers**テーブルには、ローカルディストリビューターによってサポートされるリモートパブリッシャーごとに1つの行が含まれます。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|パブリッシャーディストリビューターの名前。|  
|**distribution_db**|**sysname**|ディストリビューションデータベースの名前。|  
|**working_directory**|**nvarchar(255)**|パブリケーションのデータとスキーマファイルを格納するために使用する作業ディレクトリの名前。|  
|**security_mode**|**int**|ディストリビューターで実装されているセキュリティ モード。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証。<br /><br /> **1** = Windows 認証。|  
|**ログイン**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログイン ID です。|  
|**password**|**nvarchar (524)**|認証用のパスワード (暗号化されたもの) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。|  
|**active**|**bit**|ローカルディストリビューターがリモートパブリッシャーによって使用されているかどうかを示します。|  
|**テッド**|**bit**|リモートパブリッシャーがローカルディストリビューターと同じパスワードを使用するかどうかを示します。<br /><br /> **0** = ディストリビューターに接続するために、リモートパブリッシャーでパスワードが必要です。<br /><br /> **1** = パスワードは必要ありません。|  
|**third_party**|**bit**|パブリッシャーがインストールされているかどうかを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 示します。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストール。**1** = 異種データソース。|  
|**publisher_type**|**sysname**|パブリッシャーの種類:<br /><br /> **MSSQLSERVER**  =  MSSQLSERVER [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]文書.<br /><br /> **Oracle** = Standard oracle パブリッシャー。<br /><br /> **ORACLE gateway** = Oracle ゲートウェイパブリッシャー。|  
|**storage_connection_string**|**nvarchar (779)**|Azure SQL Database ストレージ接続文字列の値。|  

  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
