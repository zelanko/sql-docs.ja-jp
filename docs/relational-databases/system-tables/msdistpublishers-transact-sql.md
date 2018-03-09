---
title: "MSdistpublishers (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSdistpublishers
- MSdistpublishers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSdistpublishers system table
ms.assetid: 31844099-4b33-4dc9-84b4-bac70aa82598
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 39435281a7b2eb1ab26648c8b768a3abb8d4777f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msdistpublishers-transact-sql"></a>MSdistpublishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]**MSdistpublishers**テーブルには、ローカル ディストリビューターによってサポートされているリモート パブリッシャーごとに 1 つの行が含まれています。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|リモート パブリッシャーの名前です。|  
|**distribution_db**|**sysname**|ディストリビューション データベースの名前。|  
|**working_directory**|**nvarchar (255)**|パブリケーションのデータ ファイルとスキーマ ファイルを格納するために使用する作業ディレクトリの名前です。|  
|**security_mode**|**int**|ディストリビューターで実装されているセキュリティ モード。<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。<br /><br /> **1** = Windows 認証です。|  
|**ログイン**|**sysname**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証のログイン ID です。|  
|**パスワード**|**nvarchar (524)**|(暗号化) パスワード[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。|  
|**アクティブ**|**bit**|ローカル ディストリビューターがリモート パブリッシャーによって使用されているかどうかを示します。|  
|**信頼されています。**|**bit**|リモート パブリッシャーがローカル ディストリビューターと同じパスワードを使用するかどうかを示します。<br /><br /> **0** A を = ディストリビューターに接続するリモート パブリッシャーでパスワードが必要です。<br /><br /> **1** = No パスワードが必要です。|  
|**third_party**|**bit**|パブリッシャーがのインストールであるかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インストール**。1** = 異種データ ソース。|  
|**publisher_type**|**sysname**|パブリッシャーの種類:<br /><br /> **MSSQLSERVER**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。<br /><br /> **ORACLE**標準の Oracle パブリッシャーを = です。<br /><br /> **ORACLE GATEWAY** = Oracle ゲートウェイ パブリッシャーです。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
