---
title: スキーマ行セットは、OLE DB テーブル値パラメーターの変更 |Microsoft ドキュメント
description: スキーマ行セットの変更 OLE DB Table-Valued パラメーター
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- table-valued parameters (OLE DB), schema rowsets changed for (OLE DB)
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ed09bdcb3e61eaa7759c30df1901ad4954dca489
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="schema-rowsets-changed-for-ole-db-table-valued-parameters"></a>OLE DB テーブル値パラメーター向けに変更されたスキーマ行セット
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  テーブル値パラメーターをサポートするために変更または追加されたスキーマ行セットは次のとおりです。  
  
|スキーマ行セット|Description|  
|-------------------|-----------------|  
|DBSCHEMA_PROCEDURE_PARAMETERS|SS_TYPE_CATALOG_NAME および SS_TYPE_SCHEMANAME という名前の 2 つの新しい列が、行セットの末尾に追加されました。 これらの列は、今後の型に再利用できます。 TYPE_NAME 列および LOCAL_TYPE_NAME 列には、テーブル値パラメーター TABLE 型の名前が含まれます。 DATA_TYPE 列には、テーブル値パラメーターの値 DBTYPE_TABLE = 143 が含まれます。|  
|DBSCHEMA_TABLE_TYPES|この行セットは、テーブル値パラメーターをサポートするために追加されました。 これは、DBSCHEMA_TABLES と似ていますが、テーブル、ビュー、またはシノニムではなく、テーブル型のメタデータのみを返す点が異なります。 TABLE_TYPE 列の値は、'TABLE TYPE' になります。|  
|DBSCHEMA_TABLE_TYPE_PRIMARY_KEYS|この行セットは、テーブル値パラメーターをサポートするために追加されました。 これは、DBSCHEMA_PRIMARY_KEYS と似ていますが、テーブルではなく、テーブル型の主キーのメタデータのみを返す点が異なります。|  
|DBSCHEMA_TABLE_TYPE_COLUMNS|この行セットは、テーブル値パラメーターをサポートするために追加されました。 これは、DBSCHEMA_COLUMNS と似ていますが、テーブル、ビュー、またはシノニムではなく、テーブル型の列のメタデータのみを返す点が異なります。|  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB (&) #41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
