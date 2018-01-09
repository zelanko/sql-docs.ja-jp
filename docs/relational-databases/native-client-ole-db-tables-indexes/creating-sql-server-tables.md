---
title: "SQL Server テーブルを作成 |Microsoft ドキュメント"
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
- tables [OLE DB]
- SQL Server Native Client OLE DB provider, tables
- DBCOLUMNDESC usage
- adding tables
- CreateTable function
ms.assetid: a7b8d142-d76a-44d9-a583-86ac5109fbe8
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6c6c5e697044275940ac62cf9174f86f29370dc8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="creating-sql-server-tables"></a>SQL Server テーブルの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを公開、 **itabledefinition::createtable**関数を作成するコンシューマー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。 コンシューマーを使用して**CreateTable**によって生成される一意の名前を持つコンシューマーという名前のパーマネント テーブル、および永続的なまたは一時テーブルを作成する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーです。  
  
 コンシューマーを呼び出すと**itabledefinition::createtable**DBPROP_TBL_TEMPTABLE プロパティの値が VARIANT_TRUE の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがコンシューマー向けに一時テーブル名を生成します。 コンシューマー セット、 *pTableID*のパラメーター、 **CreateTable**メソッドを NULL にします。 によって生成された名前が付いた一時テーブル、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーには表示されない、**テーブル**行セット、経由でアクセスできるが、 **IOpenRowset**インターフェイス。  
  
 コンシューマーが内のテーブル名を指定すると、 *pwszName*のメンバー、 *uName*共用体の*pTableID* 、パラメーター、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]その名前を持つテーブルです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルの名前付けに関する制約が適用されるので、そのテーブル名で、パーマネント テーブル、ローカル一時テーブルまたはグローバル一時テーブルのいずれであるかを示すことができます。 詳細については、次を参照してください。 [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)です。 *PpTableID*パラメーターが NULL にすることができます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、永続的または一時的なテーブルの名前を生成できます。 コンシューマーが設定した場合、 *pTableID*パラメーターを NULL とセット*ppTableID*有効な DBID を指す\*、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが内のテーブルの生成された名前を返します、 *pwszName*のメンバー、 *uName*の値によって示される DBID の和集合*ppTableID*です。 一時的なを作成する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーという名前のテーブルでは、コンシューマーが含まれています、OLE DB テーブル プロパティ DBPROP_TBL_TEMPTABLE テーブル プロパティで参照されているセットの*rgPropertySets*パラメーター。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーという名前の一時テーブルは、ローカルです。  
  
 **CreateTable** DB_E_BADTABLEID を返します、 *eKind*のメンバー、 *pTableID*パラメーターに DBKIND_NAME を指定できません。  
  
## <a name="dbcolumndesc-usage"></a>DBCOLUMNDESC の使用方法  
 コンシューマーはいずれかを使用して、列のデータ型を指定することができます、 *pwszTypeName*メンバーまたは*wType*メンバー。 コンシューマーでのデータ型を指定する場合*pwszTypeName*、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの値を無視する*wType*です。  
  
 使用する場合、 *pwszTypeName*メンバー、コンシューマーを使用してデータ型を指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型名。 有効なデータ型名は、PROVIDER_TYPES スキーマの行セットの TYPE_NAME 列に返されるデータ型名です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでの DBTYPE の OLE DB 列挙値のサブセットを認識しません、 *wType*メンバー。 詳細については、次を参照してください。 [ITableDefinition でのデータ型マッピング](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md)です。  
  
> [!NOTE]  
>  **CreateTable**コンシューマーがいずれかに設定 DB_E_BADTYPE を返します、 *pTypeInfo*または*pclsid の値*メンバー列のデータ型を指定します。  
  
 内の列名を指定するコンシューマー、 *pwszName*のメンバー、 *uName*共用体、DBCOLUMNDESC の*dbcid*メンバー。 列名は、Unicode 文字の文字列として指定されます。 *EKind*のメンバー *dbcid* dbkind_name にする必要があります。 **CreateTable**場合は DB_E_BADCOLUMNID を返します*eKind*が有効でない*pwszName*が NULL の場合、またはの値*pwszName*が無効です[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子。  
  
 列のすべてのプロパティは、テーブルに定義されたすべての列で使用できます。 **CreateTable**競合しているプロパティの値が設定されている場合、DB_S_ERRORSOCCURRED または DB_E_ERRORSOCCURRED 返すことができます。 **CreateTable**無効な列プロパティの設定が発生するときにエラーが返されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル作成に失敗しました。  
  
 DBCOLUMNDESC の列プロパティは、次のように解釈されます。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br></br>説明 : 作成された列に ID プロパティを設定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ID プロパティをテーブル内の 1 つの列に設定できます。 VARIANT_TRUE に 1 つの列には、エラーが生成されます。 より多くのプロパティを設定時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、サーバーにテーブルを作成しようとしています。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Identity プロパティはに対してのみ有効、**整数**、**数値**、および**decimal**型の小数点以下桁数が 0 の場合。 VARIANT_TRUE に他のデータ型の列のプロパティを設定、エラーが発生時に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、サーバーにテーブルを作成しようとしています。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは DB_S_ERRORSOCCURRED を返します DBPROP_COL_AUTOINCREMENT と DBPROP_COL_NULLABLE 両方が VARIANT_TRUE と*dwOption* DBPROP_COL_NULLABLE がない DBPROPOPTIONS_REQUIRED です。 DBPROP_COL_AUTOINCREMENT と DBPROP_COL_NULLABLE 両方が VARIANT_TRUE の場合、DB_E_ERRORSOCCURRED が返されると、 *dwOption* DBPROP_COL_NULLABLE の dbpropoptions_required します。 列が定義されている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identity プロパティと、DBPROP_COL_NULLABLE *dwStatus*メンバーが DBPROPSTATUS_CONFLICTING に設定します。|  
|DBPROP_COL_DEFAULT|R/W 読み取り/書き込み<br /><br /> 既定値: なし<br /><br /> 説明 : 列に対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の DEFAULT 制約を作成します。<br /><br /> *VValue* DBPROP のメンバーには、さまざまな種類のいずれかを指定できます。 *VValue.vt*メンバーは、列のデータ型と互換性のある型を指定する必要があります。 たとえば、DBTYPE_WSTR で定義された列の既定値として BSTR N/A を定義した場合は互換性の要件が満たされます。 DBTYPE_R8 には、エラーが生成されます。 定義された列で同じ既定値を定義するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、サーバーにテーブルを作成しようとしています。|  
|DBPROP_COL_DESCRIPTION|R/W 読み取り/書き込み<br /><br /> 既定値: なし<br /><br /> 説明: DBPROP_COL_DESCRIPTION 列プロパティはによって実装されていません、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーです。<br /><br /> *DwStatus*コンシューマーが、プロパティ値を作成しようとすると、DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を返します。<br /><br /> プロパティの設定要件を満たしませんの致命的なエラー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーです。 他のすべてのパラメーター値が有効であれば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のテーブルが作成されます。|  
|DBPROP_COL_FIXEDLENGTH|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは DBPROP_COL_FIXEDLENGTH を使用してコンシューマーを使用して、列のデータ型を定義するときに、データ型のマッピングを判断する、 *wType* DBCOLUMNDESC のメンバーです。 詳細については、次を参照してください。 [ITableDefinition でのデータ型マッピング](../../relational-databases/native-client-ole-db-data-types/data-type-mapping-in-itabledefinition.md)です。|  
|DBPROP_COL_NULLABLE|R/W 読み取り/書き込み<br /><br /> 既定値: なし<br /><br /> 説明: テーブルを作成するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、プロパティが設定されている場合に、列が null 値を受け入れるかどうかを示します。 このプロパティが設定されていないときは、列が値として NULL を許容するかどうかは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定のデータベース オプション ANSI_NULLS によって決まります。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、ISO 準拠のプロバイダー。 接続されたセッションでは、ISO 準拠の動作が行われます。 DBPROP_COL_NULLABLE を設定しないと、列は NULL 値を許容します。|  
|DBPROP_COL_PRIMARYKEY|R/W 読み取り/書き込み<br /><br /> 既定値: VARIANT_FALSE 明: VARIANT_TRUE のときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー、PRIMARY KEY 制約、列を作成します。<br /><br /> 列プロパティとして定義するときは、1 つの列だけが制約を判断できます。 超える場合、単一の列には、エラーが返されます。 このプロパティを VARIANT_TRUE を設定するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが、作成しようとしています。、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル。<br /><br /> 注: コンシューマーが使用できる**iindexdefinition::createindex**を 2 つ以上の列に PRIMARY KEY 制約を作成します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは DB_S_ERRORSOCCURRED を返します DBPROP_COL_PRIMARYKEY と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE と*dwOption* DBPROP_COL_UNIQUE を利用する DBPROPOPTIONS_REQUIRED はありません。<br /><br /> DBPROP_COL_PRIMARYKEY と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE の場合、DB_E_ERRORSOCCURRED が返されると、 *dwOption* DBPROP_COL_UNIQUE の dbpropoptions_required します。 列が定義されている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identity プロパティと、DBPROP_COL_PRIMARYKEY *dwStatus*メンバーが DBPROPSTATUS_CONFLICTING に設定します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、DBPROP_COL_PRIMARYKEY と DBPROP_COL_NULLABLE 両方が VARIANT_TRUE のときにエラーが返されます。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーからエラーが返されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンシューマーが無効の列に PRIMARY KEY 制約を作成しようとしたときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。 作成される列に PRIMARY KEY 制約を定義することはできません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型**ビット**、**テキスト**、 **ntext**、および**イメージ**です。|  
|DBPROP_COL_UNIQUE|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE&lt;br&gt;&lt;/br&gt;説明 : 列に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の UNIQUE 制約を適用します。<br /><br /> 列プロパティとして定義するときは、1 つの列だけに制約が適用されます。 コンシューマーが使用できる**iindexdefinition::createindex**を 2 つ以上の列の値の組み合わせに一意の制約を適用します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは DB_S_ERRORSOCCURRED を返します DBPROP_COL_PRIMARYKEY と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE と*dwOption* DBPROPOPTIONS_REQUIRED ではありません。<br /><br /> DBPROP_COL_PRIMARYKEY と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE の場合、DB_E_ERRORSOCCURRED が返されると*dwOption* dbpropoptions_required です。 列が定義されている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identity プロパティと、DBPROP_COL_PRIMARYKEY *dwStatus*メンバーが DBPROPSTATUS_CONFLICTING に設定します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは DB_S_ERRORSOCCURRED を返します DBPROP_COL_NULLABLE と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE と*dwOption* DBPROPOPTIONS_REQUIRED ではありません。<br /><br /> DBPROP_COL_NULLABLE と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE の場合、DB_E_ERRORSOCCURRED が返されると*dwOption* dbpropoptions_required です。 列が定義されている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] identity プロパティと、DBPROP_COL_NULLABLE *dwStatus*メンバーが DBPROPSTATUS_CONFLICTING に設定します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーからエラーが返されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンシューマーが無効の列に UNIQUE 制約を作成しようとしたときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。 作成される列に UNIQUE 制約を定義することはできません、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ビット**データ型。|  
  
 コンシューマーを呼び出すと**itabledefinition::createtable**、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、テーブルのプロパティを次のように解釈します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|R/W 読み取り/書き込み<br /><br /> 既定値: VARIANT_FALSE の説明: 既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがコンシューマーによってという名前のテーブルを作成します。 ときに VARIANT_TRUE を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーがコンシューマー向けに一時テーブル名を生成します。 コンシューマー セット、 *pTableID*のパラメーター **CreateTable**を NULL にします。 *PpTableID*パラメーターは、有効なポインターを含める必要があります。|  
  
 コンシューマーが行セットが正常に作成されたテーブルで開かれることを要求する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、カーソルでサポートされている行セットを開きます。 渡されるプロパティ セットで任意の行セット プロパティを指定できます。  
  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルを作成します。  
  
```  
// This CREATE TABLE statement shows the details of the table created by   
// the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//    CONSTRAINT PK_OrderDetails  
//         PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
// The PRIMARY KEY constraint is created in an additional example.  
HRESULT CreateTable  
    (  
    ITableDefinition* pITableDefinition  
    )  
    {  
    DBID            dbidTable;  
    const ULONG     nCols = 5;  
    ULONG           nCol;  
    ULONG           nProp;  
    DBCOLUMNDESC    dbcoldesc[nCols];  
  
    HRESULT         hr;  
  
    // Set up column descriptions. First, set default property values for  
    //  the columns.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbcoldesc[nCol].pwszTypeName = NULL;  
        dbcoldesc[nCol].pTypeInfo = NULL;  
        dbcoldesc[nCol].rgPropertySets = new DBPROPSET;  
        dbcoldesc[nCol].pclsid = NULL;  
        dbcoldesc[nCol].cPropertySets = 1;  
        dbcoldesc[nCol].ulColumnSize = 0;  
        dbcoldesc[nCol].dbcid.eKind = DBKIND_NAME;  
        dbcoldesc[nCol].wType = DBTYPE_I4;  
        dbcoldesc[nCol].bPrecision = 0;  
        dbcoldesc[nCol].bScale = 0;  
  
        dbcoldesc[nCol].rgPropertySets[0].rgProperties =   
            new DBPROP[NCOLPROPS_MAX];  
        dbcoldesc[nCol].rgPropertySets[0].cProperties = NCOLPROPS_MAX;  
        dbcoldesc[nCol].rgPropertySets[0].guidPropertySet =  
            DBPROPSET_COLUMN;  
  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                dwOptions = DBPROPOPTIONS_REQUIRED;  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].colid  
                 = DB_NULLID;  
  
            VariantInit(  
                &(dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                    vValue));  
  
            dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt = VT_BOOL;  
            }  
        }  
  
    // Set the column-specific information.  
    dbcoldesc[0].dbcid.uName.pwszName = L"OrderID";  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[0].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[0].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[1].dbcid.uName.pwszName = L"ProductID";  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[1].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[1].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[2].dbcid.uName.pwszName = L"UnitPrice";  
    dbcoldesc[2].wType = DBTYPE_CY;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[2].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[2].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[3].dbcid.uName.pwszName = L"Quantity";  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[3].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[3].rgPropertySets[0].cProperties = 1;  
  
    dbcoldesc[4].dbcid.uName.pwszName = L"Discount";  
    dbcoldesc[4].wType = DBTYPE_NUMERIC;  
    dbcoldesc[4].bPrecision = 2;  
    dbcoldesc[4].bScale = 2;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].dwPropertyID =   
        DBPROP_COL_NULLABLE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[0].vValue.boolVal =   
        VARIANT_FALSE;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].dwPropertyID =   
        DBPROP_COL_DEFAULT;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.vt = VT_BSTR;  
    dbcoldesc[4].rgPropertySets[0].rgProperties[1].vValue.bstrVal =  
        SysAllocString(L"0");  
    dbcoldesc[4].rgPropertySets[0].cProperties = 2;  
  
    // Set up the dbid for OrderDetails.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    if (FAILED(hr = pITableDefinition->CreateTable(NULL, &dbidTable,  
        nCols, dbcoldesc, NULL, 0, NULL, NULL, NULL)))  
        {  
        DumpError(pITableDefinition, IID_ITableDefinition);  
        goto SAFE_EXIT;  
        }  
  
SAFE_EXIT:  
    // Clean up dynamic allocation in the property sets.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        for (nProp = 0; nProp < NCOLPROPS_MAX; nProp++)  
            {  
            if (dbcoldesc[nCol].rgPropertySets[0].rgProperties[nProp].  
                vValue.vt == VT_BSTR)  
                {  
                SysFreeString(dbcoldesc[nCol].rgPropertySets[0].  
                    rgProperties[nProp].vValue.bstrVal);  
                }  
            }  
  
        delete [] dbcoldesc[nCol].rgPropertySets[0].rgProperties;  
        delete [] dbcoldesc[nCol].rgPropertySets;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
