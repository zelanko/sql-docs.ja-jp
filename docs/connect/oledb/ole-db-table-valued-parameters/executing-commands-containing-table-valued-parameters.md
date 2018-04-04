---
title: テーブル値パラメーターを含むコマンドを実行する |Microsoft ドキュメント
description: テーブル値パラメーターを含むコマンドを実行します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 007e0e52605d1d3aecc4216146abff3e73bf7ea4
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="executing-commands-containing-table-valued-parameters"></a>テーブル値パラメーターを含むコマンドの実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  テーブル値パラメーターを使用してコマンドを実行するには、2 つのフェーズが必要です。  
  
1.  パラメーターの型を指定する。  
  
2.  パラメーター データをバインドする。  
  
## <a name="table-valued-parameter-specification"></a>テーブル値パラメーターの指定  
 コンシューマーは、テーブル値パラメーターの型を指定できます。 この情報には、テーブル値パラメーターの型名が含まれます。 接続の現在の既定のスキーマにテーブル値パラメーターのユーザー定義テーブル型がない場合は、スキーマ名も含まれます。 サーバーのサポートによって、コンシューマー可能性がありも指定省略可能なメタデータについては、列の順序など、特定の列のすべての行が既定値を持つことを示すことができます。  
  
 テーブル値パラメーターを指定するには、コンシューマーは ISSCommandWithParamter::SetParameterInfo、して必要に応じて isscommandwithparameters::setparameterproperties です。 テーブル値パラメーターの場合、*して*DBPARAMBINDINFO 構造体のフィールドには DBTYPE_TABLE の値。 *UlParamSize*にフィールドが設定されている ~ 0 その長さを示すためには不明です。 Isscommandwithparameters::setparameterproperties を通じて、スキーマ名、型名、列の順序、および既定の列などのテーブル値パラメーターの特定のプロパティを設定できます。  
  
## <a name="table-valued-parameter-binding"></a>テーブル値パラメーターのバインド  
 テーブル値パラメーターには、任意の行セット オブジェクトを指定できます。 プロバイダーは、実行中、このオブジェクトからテーブル値パラメーターを読み取って、サーバーに送信します。  
  
 テーブル値パラメーターをバインドするには、コンシューマーは、iaccessor::createaccessor を呼び出します。 *WType*テーブル値パラメーターの DBBINDING 構造体のフィールドは DBTYPE_TABLE に設定します。 *PObject* DBBINDING 構造体のメンバーは、NULL 以外の場合、および*pObject*の*iid*メンバーは IID_IRowset、またはその他のテーブル値パラメーター行セット オブジェクトに設定インターフェイス。 DBBINDING 構造体の残りのフィールドは、ストリームされた Blob に対して設定すると、同じように設定する必要があります。  
  
 テーブル値パラメーターと、テーブル値パラメーターに関連付けられる行セット オブジェクトのバインドでは、次の制限が適用されます。  
  
-   テーブル値パラメーターの行セット列データに許容される状態値は DBSTATUS_S_ISNULL と DBSTATUS_S_OK だけです。 DBSTATUS_S_DEFAULT、障害が発生し、バインド状態値が DBSTATUS_E_BADSTATUS に設定されます。  
  
-   テーブル値パラメーターは DBSTATUS_S_DEFAULT 状態でマークできます。 有効な値は DBSTATUS_S_DEFAULT と DBSTATUS_S_OK だけです。 状態が DBSTATUS_S_DEFAULT に設定された場合、テーブル値パラメーターの値は、空のテーブルに対応します。  
  
-   テーブル値パラメーターの読み取り専用列 (ID 列または計算列) は、SSPROP_PARAM_TABLE_DEFAULT_COLUMNS プロパティを使って、既定としてマークする必要があります。 既定値を持つ列も、特定のテーブル値パラメーターの列データに既定値を使用できるように、SSPROP_PARAM_TABLE_DEFAULT_COLUMNS プロパティで、既定としてマークする必要があります。 既定としてマークされた列にバインドされたデータ値は、プロバイダーによって無視されます。  
  
-   SSPROP_PARAM_TABLE_DEFAULT も設定されない限り、データは、DBPROP_COL_AUTOINCREMENT または SSPROP_COL_COMPUTED が設定された列を想定して、サーバーに送信されます。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用してテーブル値パラメーター (&) #40 です。 OLE DB &#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
