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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2c19f2d8e75a3c9744318d65683b29d1d84857ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907424"
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  **Msdistpublishers**テーブルには、ローカルディストリビューターによってサポートされるリモートパブリッシャーごとに1つの行が含まれます。 このテーブルは、 **msdb**データベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|パブリッシャーディストリビューターの名前。|  
|**distribution_db**|**sysname**|ディストリビューションデータベースの名前。|  
|**working_directory**|**nvarchar(255)**|パブリケーションのデータとスキーマファイルを格納するために使用する作業ディレクトリの名前。|  
|**security_mode**|**int**|ディストリビューターで実装されているセキュリティ モード。<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証。<br /><br /> **1** = Windows 認証。|  
|**ログイン**|**sysname**|
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログイン ID です。|  
|**入力**|**nvarchar (524)**|認証用の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パスワード (暗号化されたもの)。|  
|**能動的**|**bit**|ローカルディストリビューターがリモートパブリッシャーによって使用されているかどうかを示します。|  
|**テッド**|**bit**|リモートパブリッシャーがローカルディストリビューターと同じパスワードを使用するかどうかを示します。<br /><br /> **0** = ディストリビューターに接続するために、リモートパブリッシャーでパスワードが必要です。<br /><br /> **1** = パスワードは必要ありません。|  
|**third_party**|**bit**|パブリッシャーがインストールされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]かどうかを示します。<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインストール。**1** = 異種データソース。|  
|**publisher_type**|**sysname**|パブリッシャーの種類:<br /><br /> **** =  MSSQLSERVER[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャー。<br /><br /> **Oracle** = Standard oracle パブリッシャー。<br /><br /> **ORACLE gateway** = Oracle ゲートウェイパブリッシャー。|  
|**storage_connection_string**|**nvarchar (779)**|Azure SQL Database ストレージ接続文字列の値。|  

  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
