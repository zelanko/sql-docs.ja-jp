---
title: SQL Server テーブルに列の追加 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- columns [OLE DB]
- AddColumn function
- SQL Server Native Client OLE DB provider, columns
- adding columns
ms.assetid: 22bae18a-bc9d-4617-8660-ed8b17a468d4
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e79886f09783737a392fa67899feb59cd7deb2a1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425271"
---
# <a name="adding-a-column-to-a-sql-server-table"></a>SQL Server テーブルへの列の追加
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開、 **itabledefinition::addcolumn**関数。 これにより、列を追加するコンシューマー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。  
  
 列を追加すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、テーブル、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのコンシューマーは次の制約します。  
  
-   DBPROP_COL_AUTOINCREMENT が VARIANT_TRUE の場合、DBPROP_COL_NULLABLE を VARIANT_FALSE にする必要があります。  
  
-   使用して、列が定義されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **タイムスタンプ**データ型、DBPROP_COL_NULLABLE は VARIANT_FALSE をある必要があります。  
  
-   それ以外の列定義の場合、DBPROP_COL_NULLABLE は VARIANT_TRUE にする必要があります。  
  
 コンシューマーでは、テーブル名を指定の Unicode 文字の文字列として、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* DBKIND_NAME にする必要があります。  
  
 新しい列名が Unicode 文字列で指定された、 *pwszName*のメンバー、 *uName*共用体の*dbcid* DBCOLUMNDESC パラメーターのメンバー*pColumnDesc*します。 *EKind*メンバーは DBKIND_NAME をする必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブルとパーティション インデックス](tables-and-indexes.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)  
  
  
