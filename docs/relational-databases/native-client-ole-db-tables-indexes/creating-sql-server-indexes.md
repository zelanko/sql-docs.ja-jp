---
title: "SQL Server インデックスの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-tables-indexes
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
caps.latest.revision: "32"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72d112e951b940a0eb424e79bc431237bcf06d0d
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="creating-sql-server-indexes"></a>SQL Server インデックスの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを公開、 **iindexdefinition::createindex**関数を新しいインデックスを定義するコンシューマー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、インデックスまたは制約のいずれかとしてテーブルのインデックスを作成します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、制約を作成する権限がテーブルの所有者、データベースの所有者、および特定の管理ロールのメンバーに許可されます。 テーブルにインデックスを作成できるのは、既定では、テーブルの所有者だけです。 したがって、成功または失敗の**CreateIndex**だけでなく、アプリケーション ユーザーのアクセス権に作成されたインデックスの種類にも依存します。  
  
 コンシューマーでは、テーブル名を指定の Unicode 文字の文字列として、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* dbkind_name にする必要があります。  
  
 *PIndexID*を NULL にする場合は、パラメーターができる、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、インデックスの一意の名前を作成します。 コンシューマーに DBID への有効なポインターを指定して、インデックスの名前をキャプチャすることができます、 *ppIndexID*パラメーター。  
  
 コンシューマーは、Unicode 文字の文字列としてインデックスの名前を指定できます、 *pwszName*のメンバー、 *uName*共用体の*pIndexID*パラメーター。 *EKind*のメンバー *pIndexID* dbkind_name にする必要があります。  
  
 コンシューマーは、インデックスに参加する列または複数の列を名前で指定します。 それぞれの DBINDEXCOLUMNDESC 構造で使用される**CreateIndex**、 *eKind*のメンバー、 *pColumnID* dbkind_name にする必要があります。 Unicode 文字の文字列として列の名前が指定されて、 *pwszName*のメンバー、 *uName*共用体の*pColumnID*です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックス内の値に基づいて昇順サポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがコンシューマー、DBINDEXCOLUMNDESC 構造体に DBINDEX_COL_ORDER_DESC を指定する場合、E_INVALIDARG を返します。  
  
 **CreateIndex**インデックスのプロパティを次のように解釈します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_CLUSTERED|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : インデックスのクラスター化を制御します。<br /><br /> VARIANT_TRUE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a clustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、どのテーブルでもクラスター化インデックスは 1 つしかサポートされません。<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、非クラスター化インデックスを作成しようとしています、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。|  
|DBPROP_INDEX_FILLFACTOR|R/W 読み取り/書き込み<br /><br /> 既定値: 0<br /><br /> 説明 : インデックス ページの格納に使用する割合を指定します。 詳細については、次を参照してください。 [CREATE INDEX](../../t-sql/statements/create-index-transact-sql.md)です。<br /><br /> バリアントの型は VT_I4 です。 値は 1 ～ 100 にする必要があります。|  
|DBPROP_INDEX_INITIALIZE|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_NULLCOLLATION|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_NULLS|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_PRIMARYKEY|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE&lt;br&gt;&lt;/br&gt;説明 : 参照整合性 (PRIMARY KEY 制約) としてインデックスを作成します。<br /><br /> VARIANT_TRUE: インデックスは、テーブルの PRIMARY KEY 制約をサポートするために作成されます。 列には NULL 値を許容しないでください。<br /><br /> VARIANT_FALSE: インデックスは、テーブル内の行値の PRIMARY KEY 制約としては使用されません。|  
|DBPROP_INDEX_SORTBOOKMARKS|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_TEMPINDEX|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_TYPE|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_UNIQUE|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : インデックスに参加する列または複数の列に、UNIQUE 制約としてインデックスを作成します。<br /><br /> VARIANT_TRUE: インデックスを使用して、テーブル内の行値を一意に制約します。<br /><br /> VARIANT_FALSE: インデックスでは、行値が一意に制約されません。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERINDEX、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次のデータ ソース情報のプロパティを定義します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|SSPROP_INDEX_XML|型 : VT_BOOL (R/W)<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : IIndexDefinition::CreateIndex のときに、このプロパティの値に VARIANT_TRUE を指定すると、インデックス対象の列に対応するプライマリ XML インデックスが作成されます。 このプロパティが VARIANT_TRUE の場合、cIndexColumnDescs を 1 にする必要があります。それ以外の値を指定するとエラーが発生します。|  
  
 次の例では、主キー インデックスを作成します。  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>参照  
 [テーブルとパーティション インデックス](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
