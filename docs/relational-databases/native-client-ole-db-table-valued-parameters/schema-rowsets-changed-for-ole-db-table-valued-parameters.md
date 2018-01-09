---
title: "スキーマ行セットは、OLE DB テーブル値パラメーターの変更 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
ms.assetid: 581e3ead-53db-44da-8718-f3fc4b5108f1
caps.latest.revision: "16"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d3a0a5903f81b459647ccc28a3af383a051917d3
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>OLE DB テーブル値パラメーター向けに変更されたスキーマ行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  テーブル値パラメーターをサポートするために変更または追加されたスキーマ行セットは次のとおりです。  
  
|スキーマ行セット|Description|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|SS_TYPE_CATALOG_NAME および SS_TYPE_SCHEMANAME という名前の 2 つの新しい列が、行セットの末尾に追加されました。 これらの列は、今後の型に再利用できます。 TYPE_NAME 列および LOCAL_TYPE_NAME 列には、テーブル値パラメーター TABLE 型の名前が含まれます。 DATA_TYPE 列には、テーブル値パラメーターの値 DBTYPE_TABLE = 143 が含まれます。|  
|DBSCHEMA_TABLE_TYPES|この行セットは、テーブル値パラメーターをサポートするために追加されました。 これは、DBSCHEMA_TABLES と似ていますが、テーブル、ビュー、またはシノニムではなく、テーブル型のメタデータのみを返す点が異なります。 TABLE_TYPE 列の値は、'TABLE TYPE' になります。|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|この行セットは、テーブル値パラメーターをサポートするために追加されました。 これは、DBSCHEMA_PRIMARY_KEYS と似ていますが、テーブルではなく、テーブル型の主キーのメタデータのみを返す点が異なります。|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|この行セットは、テーブル値パラメーターをサポートするために追加されました。 これは、DBSCHEMA_COLUMNS と似ていますが、テーブル、ビュー、またはシノニムではなく、テーブル型の列のメタデータのみを返す点が異なります。|  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター (&) #40 です。 OLE DB &#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
