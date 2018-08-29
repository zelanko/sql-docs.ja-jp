---
title: sp_xml_removedocument (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_xml_removedocument_TSQL
- sp_xml_removedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_removedocument
ms.assetid: f9dca50a-8baf-4170-90bc-e72783ce5b73
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed76914663049816d7877e6fe4e3ad3709d2f3b4
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43027093"
---
# <a name="spxmlremovedocument-transact-sql"></a>sp_xml_removedocument (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ドキュメント ハンドルで指定された XML ドキュメントの内部表現を削除し、ドキュメント ハンドルを無効にします。  
  
> [!NOTE]  
>  解析済みドキュメントがの内部キャッシュに格納されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 MSXML パーサー (Msxmlsql.dll) では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に割り当てられている総メモリの 8 分の 1 が使用されます。 メモリ不足を回避するには、実行**sp_xml_removedocument**メモリを解放します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_xml_removedocument hdoc  
```  
  
## <a name="arguments"></a>引数  
 *hdoc*  
 新しく作成されたドキュメントへのハンドルを指定します。 有効でないハンドルを指定するとエラーが返されます。 *hdoc*は整数です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、XML ドキュメントの内部表現を削除します。 この XML ドキュメントのハンドルは、入力値として指定します。  
  
```  
EXEC sp_xml_removedocument @hdoc;  
```  
  
## <a name="see-also"></a>参照      
 <br>[システム ストアド プロシージャ (TRANSACT-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
 <br>[XML ストアド プロシージャ (TRANSACT-SQL)](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)
 <br>[sys.dm_exec_xml_handles (TRANSACT-SQL)](../system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)
 <br>[sp_xml_preparedocument(Transact-SQL)](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[OPENXML (TRANSACT-SQL)](../../t-sql/functions/openxml-transact-sql.md)
  
  
