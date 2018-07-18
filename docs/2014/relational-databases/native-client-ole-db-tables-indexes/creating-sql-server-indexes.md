---
title: SQL Server インデックスの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2f7d53307582dbacab0d4231a7f0a13710bd84a
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37425401"
---
# <a name="creating-sql-server-indexes"></a>SQL Server インデックスの作成
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開、 **iindexdefinition::createindex**関数を新しいインデックスを定義するコンシューマー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、インデックスまたは制約としてテーブルのインデックスを作成します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、制約を作成する権限がテーブルの所有者、データベースの所有者、および特定の管理ロールのメンバーに許可されます。 テーブルにインデックスを作成できるのは、既定では、テーブルの所有者だけです。 そのため、成功または失敗の**CreateIndex**作成されたインデックスの種類にも、アプリケーション ユーザーのアクセス権だけでなくによって異なります。  
  
 コンシューマーでは、テーブル名を指定の Unicode 文字の文字列として、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* DBKIND_NAME にする必要があります。  
  
 *PIndexID*パラメーターは、NULL にしてがの場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、インデックスの一意の名前を作成します。 コンシューマーに DBID への有効なポインターを指定することで、インデックスの名前をキャプチャすることができます、 *ppIndexID*パラメーター。  
  
 コンシューマーは、Unicode 文字列でインデックスの名前を指定できます、 *pwszName*のメンバー、 *uName*共用体の*pIndexID*パラメーター。 *EKind*のメンバー *pIndexID* DBKIND_NAME にする必要があります。  
  
 コンシューマーは、インデックスに参加する列または複数の列を名前で指定します。 使用される各 DBINDEXCOLUMNDESC 構造の**CreateIndex**、 *eKind*のメンバー、 *pColumnID* DBKIND_NAME にする必要があります。 列の名前は Unicode 文字列で指定された、 *pwszName*のメンバー、 *uName*共用体の*pColumnID*します。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックス内の値に基づいて昇順のサポート。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがコンシューマーの DBINDEXCOLUMNDESC 構造体に DBINDEX_COL_ORDER_DESC を指定する場合、E_INVALIDARG を返します。  
  
 **CreateIndex**インデックスのプロパティを次のように解釈します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|DBPROP_INDEX_AUTOUPDATE|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_CLUSTERED|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : インデックスのクラスター化を制御します。<br /><br /> VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが、クラスター化インデックスを作成しようとしています。、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、どのテーブルでもクラスター化インデックスは 1 つしかサポートされません。<br /><br /> VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが、非クラスター化インデックスを作成しようとしています。、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。|  
|DBPROP_INDEX_FILLFACTOR|R/W 読み取り/書き込み<br /><br /> 既定値: 0<br /><br /> 説明 : インデックス ページの格納に使用する割合を指定します。 詳細については、次を参照してください。 [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql)します。<br /><br /> バリアントの型は VT_I4 です。 値は 1 ～ 100 にする必要があります。|  
|DBPROP_INDEX_INITIALIZE|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_NULLCOLLATION|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_NULLS|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_PRIMARYKEY|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE&lt;br&gt;&lt;/br&gt;説明 : 参照整合性 (PRIMARY KEY 制約) としてインデックスを作成します。<br /><br /> VARIANT_TRUE: インデックスは、テーブルの PRIMARY KEY 制約をサポートするために作成されます。 列には NULL 値を許容しないでください。<br /><br /> VARIANT_FALSE: インデックスは、テーブル内の行値の PRIMARY KEY 制約としては使用されません。|  
|DBPROP_INDEX_SORTBOOKMARKS|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_TEMPINDEX|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_TYPE|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがこのプロパティをサポートしていません。 プロパティを設定しようとしています。 **CreateIndex** DB_S_ERRORSOCCURRED の戻り値が発生します。 *DwStatus*プロパティ構造体のメンバー DBPROPSTATUS_BADVALUE が示されます。|  
|DBPROP_INDEX_UNIQUE|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明 : インデックスに参加する列または複数の列に、UNIQUE 制約としてインデックスを作成します。<br /><br /> VARIANT_TRUE: インデックスを使用して、テーブル内の行値を一意に制約します。<br /><br /> VARIANT_FALSE: インデックスでは、行値が一意に制約されません。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERINDEX、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次のデータ ソース情報のプロパティを定義します。  
  
|プロパティ ID|説明|  
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
 [テーブルとインデックス](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
