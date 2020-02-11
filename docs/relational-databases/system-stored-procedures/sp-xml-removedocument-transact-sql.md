---
title: sp_xml_removedocument (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_xml_removedocument_TSQL
- sp_xml_removedocument
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xml_removedocument
ms.assetid: f9dca50a-8baf-4170-90bc-e72783ce5b73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6219f18bee08d5c20431cb87a2cb30795c515d7a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67950473"
---
# <a name="sp_xml_removedocument-transact-sql"></a>sp_xml_removedocument (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ドキュメント ハンドルで指定された XML ドキュメントの内部表現を削除し、ドキュメント ハンドルを無効にします。  
  
> [!NOTE]  
>  解析されたドキュメントは、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部キャッシュに格納されます。 MSXML パーサー (Msxmlsql.dll) では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に割り当てられている総メモリの 8 分の 1 が使用されます。 メモリが不足しないようにするには、 **sp_xml_removedocument**を実行してメモリを解放します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_xml_removedocument hdoc  
```  
  
## <a name="arguments"></a>引数  
 *hdoc*  
 新しく作成されたドキュメントへのハンドルを指定します。 無効なハンドルはエラーを返します。 *hdoc*は整数です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、XML ドキュメントの内部表現を削除します。 ドキュメントへのハンドルは入力として提供されます。  
  
```  
EXEC sp_xml_removedocument @hdoc;  
```  
  
## <a name="see-also"></a>参照      
 <br>[システムストアドプロシージャ (Transact-sql)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)
 <br>[XML ストアドプロシージャ (Transact-sql)](../../relational-databases/system-stored-procedures/xml-stored-procedures-transact-sql.md)
 <br>[dm_exec_xml_handles (Transact-sql)](../system-dynamic-management-views/sys-dm-exec-xml-handles-transact-sql.md)
 <br>[sp_xml_preparedocument (Transact-sql)](../../relational-databases/system-stored-procedures/sp-xml-preparedocument-transact-sql.md)
 <br>[OPENXML (Transact-SQL)](../../t-sql/functions/openxml-transact-sql.md)
  
  
