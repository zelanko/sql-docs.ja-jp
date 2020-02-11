---
title: SQL Server Index | を削除するMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- removing indexes
- deleting indexes
- DropIndex function
- dropping indexes
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
ms.assetid: add3ba14-10b1-4723-b7c0-3e83689e9fdd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14b54b80d18b79092ab46055477b59cb4ea6d5ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046394"
---
# <a name="dropping-a-sql-server-index"></a>SQL Server インデックスの削除
  Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、 **iindexdefinition::D ropindex**関数を公開します。 コンシューマーはこの関数を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルからインデックスを削除できます。  
  
 Native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client OLE DB プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]主キーと一意の制約をインデックスとして公開します。 テーブル所有者、データベース所有者、一部の管理ロールのメンバーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルを変更して、制約を削除できます。 既定では、テーブル所有者だけが既存のインデックスを削除できます。 したがって、**DropIndex** が成功するか失敗するかは、アプリケーション ユーザーのアクセス権だけでなく、指定されたインデックスの種類によっても異なります。  
  
 コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。 
  *pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。  
  
 インデックス名は、*pIndexID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定します。 
  *pIndexID* の *eKind* メンバーを DBKIND_NAME にする必要があります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、 *pIndexID*が null の場合にテーブルのすべてのインデックスを削除する OLE DB 機能はサポートされていません。 
  *pIndexID* が NULL の場合、E_INVALIDARG を返します。  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-table-transact-sql)   
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
  
