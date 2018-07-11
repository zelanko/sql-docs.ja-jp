---
title: テーブル値パラメーターを含むコマンドの実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
ms.assetid: 7ecba6f6-fe7a-462a-9aa3-d5115b6d4529
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 943dba9ff3fbd04e8344ac4d325114ee9f05a2e2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37428353"
---
# <a name="executing-commands-containing-table-valued-parameters"></a>テーブル値パラメーターを含むコマンドの実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  テーブル値パラメーターを含むコマンドを実行するには、次の 2 つのフェーズが必要になります。  
  
1.  パラメーターの型を指定する。  
  
2.  パラメーター データをバインドする。  
  
## <a name="table-valued-parameter-specification"></a>テーブル値パラメーターの指定  
 コンシューマーは、テーブル値パラメーターの型を指定できます。 この情報には、テーブル値パラメーターの型名が含まれます。 また、テーブル値パラメーターのユーザー定義テーブル型が接続の現在の既定のスキーマにない場合は、スキーマ名も含まれます。 サーバーでサポートされているかどうかに応じて、コンシューマーでは、省略可能なメタデータ情報 (列の順序など) を指定したり、特定の列のすべての行に既定値が設定されるよう指定したりすることもできます。  
  
 テーブル値パラメーターを指定するには、コンシューマーは ISSCommandWithParamter::SetParameterInfo を呼び出すし、isscommandwithparameters::setparameterproperties を必要に応じて呼び出します。 テーブル値パラメーターの場合、*して*DBPARAMBINDINFO 構造体のフィールドは、dbtype_table から DBTYPE_TABLE の値を持ちます。 *UlParamSize*にフィールドが設定されている ~ 0 その長さを示すためには不明です。 Isscommandwithparameters::setparameterproperties を通じて、スキーマ名、型名、列の順序、および既定の列などのテーブル値パラメーターの特定のプロパティを設定できます。  
  
## <a name="table-valued-parameter-binding"></a>テーブル値パラメーターのバインド  
 テーブル値パラメーターには、任意の行セット オブジェクトを指定できます。 プロバイダーは、実行中、このオブジェクトからテーブル値パラメーターを読み取って、サーバーに送信します。  
  
 テーブル値パラメーターをバインドするには、コンシューマーは、iaccessor::createaccessor を呼び出します。 *WType*テーブル値パラメーターの DBBINDING 構造体のフィールドは、dbtype_table から DBTYPE_TABLE に設定されます。 *PObject* DBBINDING 構造体のメンバーが NULL 以外の場合、および*pObject*の*iid*メンバーは IID_IRowset、またはその他のテーブル値パラメーター行セット オブジェクトに設定インターフェイス。 DBBINDING 構造体の残りのフィールドは、ストリームされた BLOB の場合と同じように設定する必要があります。  
  
 テーブル値パラメーターと、テーブル値パラメーターに関連付けられる行セット オブジェクトのバインドでは、次の制限が適用されます。  
  
-   テーブル値パラメーターの行セット列データに許容される状態値は DBSTATUS_S_ISNULL と DBSTATUS_S_OK だけです。 DBSTATUS_S_DEFAULT、障害が発生し、バインド状態値が DBSTATUS_E_BADSTATUS に設定されます。  
  
-   テーブル値パラメーターは DBSTATUS_S_DEFAULT 状態でマークできます。 有効な値は DBSTATUS_S_DEFAULT と DBSTATUS_S_OK だけです。 状態が DBSTATUS_S_DEFAULT に設定された場合、テーブル値パラメーターの値は、空のテーブルに対応します。  
  
-   テーブル値パラメーターの読み取り専用列 (ID 列または計算列) は、SSPROP_PARAM_TABLE_DEFAULT_COLUMNS プロパティを使って、既定としてマークする必要があります。 既定値を持つ列も、特定のテーブル値パラメーターの列データに既定値を使用できるように、SSPROP_PARAM_TABLE_DEFAULT_COLUMNS プロパティで、既定としてマークする必要があります。 既定としてマークされた列にバインドされたデータ値は、プロバイダーによって無視されます。  
  
-   SSPROP_PARAM_TABLE_DEFAULT も設定されない限り、データは、DBPROP_COL_AUTOINCREMENT または SSPROP_COL_COMPUTED が設定された列を想定して、サーバーに送信されます。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [テーブル値パラメーターを使用して、 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
