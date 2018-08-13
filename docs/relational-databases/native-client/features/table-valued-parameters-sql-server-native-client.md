---
title: テーブル値パラメーター (SQL Server Native Client) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, table-valued parameters
- table-valued parameters (SQL Server Native Client)
ms.assetid: 5ee6bdcd-0309-4a20-b5c2-0e6b6839f34f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 256b28ad04115cbbdcbcde9bda545f27dfe51cc5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39562986"
---
# <a name="table-valued-parameters-sql-server-native-client"></a>テーブル値パラメーター (SQL Server Native Client)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] で導入されたテーブル値パラメーターを使用すると、複数行のデータを効率的にサーバーに渡すことができます。 テーブル値パラメーターの機能はパラメーター配列に似ていますが、より柔軟性が高く、[!INCLUDE[tsql](../../../includes/tsql-md.md)] との統合も緊密です。また、多くの場合、パフォーマンスが向上します。 テーブル値パラメーターはセットベースの操作にも使用できますが、パラメーター配列は使用できません。  
  
 テーブル値パラメーターと ODBC については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)します。  
  
 テーブル値パラメーターおよび OLE DB の詳細については、次を参照してください。[テーブル値パラメーター &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
