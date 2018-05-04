---
title: sys.server_sql_modules (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.server_sql_modules
- sys.server_sql_modules_TSQL
- server_sql_modules_TSQL
- server_sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_sql_modules catalog view
ms.assetid: 9ef9a8b9-c470-4a61-b0c4-ee24ad871d63
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 55712107ed0403caf3b690496814369873cf027c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysserversqlmodules-transact-sql"></a>sys.server_sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  一連の TR タイプのサーバー レベル トリガー用の SQL モジュールを保持します。 このリレーションは sys.server_triggers に結合できます。 組 (object_id) はリレーションのキーです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|このモジュールが定義されているサーバー レベル トリガーに戻される FOREIGN KEY 参照です。|  
|**definition**|**nvarchar(max)**|このモジュールを定義する SQL テキスト。<br /><br /> NULL は、暗号化されていることを示します。|  
|**uses_ansi_nulls**|**bit**|モジュールは ANSI NULLS 設定オプションを ON に設定して作成されました。|  
|**uses_quoted_identifier**|**bit**|モジュールは QUOTED IDENTIFIER 設定オプションを ON に設定して作成されました。|  
|**execute_as_principal_id**|**int**|EXECUTE AS サーバー プリンシパルの ID。<br /><br /> 既定、または EXECUTE AS CALLER の場合は、NULL です。<br /><br /> 場合は、指定したプリンシパルの ID AS SELF EXECUTE AS の実行のプリンシパル 2 = EXECUTE AS OWNER。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
