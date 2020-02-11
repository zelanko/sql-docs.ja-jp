---
title: SQLProcedures |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedures function
ms.assetid: ec41f017-f5e0-40ef-913a-65d206068631
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0001f1d6e45e855b884028a595a2b61263c2e58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63046686"
---
# <a name="sqlprocedures"></a>SQLProcedures
  すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャは値を返します。 **Sqlprocedures**は、結果セット列 PROCEDURE_TYPE の SQL_PT_FUNCTION を報告します。  
  
 **Sqlprocedures**は *、CatalogName、SchemaName、* または*ProcName*パラメーターの値が存在するかどうかを SQL_SUCCESS 返します。 これらのパラメーターで無効な値が使用されている場合、 **Sqlfetch**は SQL_NO_DATA を返します。  
  
 **Sqlprocedures**は、静的サーバーカーソルで実行できます。 更新可能なカーソル (動的カーソルまたはキーセットカーソル) で**Sqlprocedures**を実行しようとすると、カーソルの種類が変更されたことを示す SQL_SUCCESS_WITH_INFO が返されます。  
  
 **Sqlprocedures**は、名前が*ProcName*に一致し、現在のユーザーが実行できる、または現在のユーザーが VIEW DEFINITION 権限を許可されているプロシージャに関する情報を返します。  
  
## <a name="see-also"></a>参照  
 [SQLProcedures 関数](https://go.microsoft.com/fwlink/?LinkId=59364)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
