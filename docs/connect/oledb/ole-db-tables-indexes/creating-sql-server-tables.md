---
title: SQL Server テーブルを作成 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用して SQL Server テーブルを作成します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-tables-indexes
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- OLE DB Driver for SQL Server, tables
- DBCOLUMNDESC usage
- adding tables
- CreateTable function
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 998b1d4c18ec626a7ef48a8ff141bdfa1e2fdd36
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="creating-sql-server-tables"></a>SQL Server テーブルの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  OLE DB Driver for SQL Server を公開、 **itabledefinition::createtable**関数を作成するコンシューマー[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル。 コンシューマーを使用して**CreateTable**を SQL Server の OLE DB ドライバーによって生成される一意の名前を持つコンシューマーという名前のパーマネント テーブル、および永続的なまたは一時テーブルを作成します。  
  
 コンシューマーを呼び出すと**itabledefinition::createtable**DBPROP_TBL_TEMPTABLE プロパティの値は VARIANT_TRUE、OLE DB Driver SQL Server コンシューマー向けに一時テーブル名を生成する場合は、します。 コンシューマー セット、 *pTableID*のパラメーター、 **CreateTable**メソッドを NULL にします。 SQL Server の OLE DB ドライバーによって生成された名前が付いた一時テーブルが表示されない、**テーブル**行セット、経由でアクセスできるが、 **IOpenRowset**インターフェイスです。  
  
 コンシューマーが内のテーブル名を指定すると、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーターを OLE DB Driver for SQL Server の作成、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]その名前を持つテーブルです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルの名前付けに関する制約が適用されるので、そのテーブル名で、パーマネント テーブル、ローカル一時テーブルまたはグローバル一時テーブルのいずれであるかを示すことができます。 詳細については、次を参照してください。 [CREATE TABLE](../../../t-sql/statements/create-table-transact-sql.md)です。 *PpTableID*パラメーターが NULL にすることができます。  
  
 SQL Server の OLE DB Driver は、永続的または一時的なテーブルの名前を生成できます。 コンシューマーが設定した場合、 *pTableID*パラメーターを NULL とセット*ppTableID*有効な DBID を指す\*、OLE DB Driver for SQL Server が、で生成されたテーブルの名前を返します*pwszName*のメンバー、 *uName* DBID の和集合がの値が指す*ppTableID*です。 コンシューマーには、一時的な OLE DB Driver for SQL Server 名前付きのテーブルを作成するテーブル プロパティで参照されているセットの OLE DB テーブル プロパティ DBPROP_TBL_TEMPTABLE が含まれます、 *rgPropertySets*パラメーター。 OLE DB Driver for SQL Server という名前の一時テーブルは、ローカルです。  
  
 **CreateTable** DB_E_BADTABLEID を返します、 *eKind*のメンバー、 *pTableID*パラメーターに DBKIND_NAME を指定できません。  
  
## <a name="dbcolumndesc-usage"></a>DBCOLUMNDESC の使用方法  
 コンシューマーはいずれかを使用して、列のデータ型を指定することができます、 *pwszTypeName*メンバーまたは*wType*メンバー。 コンシューマーでのデータ型を指定する場合*pwszTypeName*、SQL Server の OLE DB Driver は、の値を無視*wType*です。  
  
 使用する場合、 *pwszTypeName*メンバー、コンシューマーを使用してデータ型を指定する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型名。 有効なデータ型名は、PROVIDER_TYPES スキーマの行セットの TYPE_NAME 列に返されるデータ型名です。  
  
 SQL Server の OLE DB ドライバーの DBTYPE の OLE DB 列挙値のサブセットを認識しません、 *wType*メンバー。 詳細については、次を参照してください。 [ITableDefinition でのデータ型マッピング](../../oledb/ole-db-data-types/data-type-mapping-in-itabledefinition.md)です。  
  
> [!NOTE]  
>  **CreateTable**コンシューマーがいずれかに設定 DB_E_BADTYPE を返します、 *pTypeInfo*または*pclsid の値*メンバー列のデータ型を指定します。  
  
 内の列名を指定するコンシューマー、 *pwszName*のメンバー、 *uName*共用体、DBCOLUMNDESC の*dbcid*メンバー。 列名は、Unicode 文字の文字列として指定されます。 *EKind*のメンバー *dbcid* dbkind_name にする必要があります。 **CreateTable**場合は DB_E_BADCOLUMNID を返します*eKind*が有効でない*pwszName*が NULL の場合、またはの値*pwszName*が無効です[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]識別子。  
  
 列のすべてのプロパティは、テーブルに定義されたすべての列で使用できます。 **CreateTable**競合しているプロパティの値が設定されている場合、DB_S_ERRORSOCCURRED または DB_E_ERRORSOCCURRED 返すことができます。 **CreateTable**無効な列プロパティの設定が発生するときにエラーが返されます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル作成に失敗しました。  
  
 DBCOLUMNDESC の列プロパティは、次のように解釈されます。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_COL_AUTOINCREMENT|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br></br>説明 : 作成された列に ID プロパティを設定します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、ID プロパティをテーブル内の 1 つの列に設定できます。 超える場合、OLE DB Driver for SQL Server が、サーバーにテーブルを作成しようとしたときに、1 つの列によってエラーが発生を VARIANT_TRUE にプロパティを設定します。<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Identity プロパティはに対してのみ有効、**整数**、**数値**、および**decimal**型の小数点以下桁数が 0 の場合。 その他の任意のデータ型の列を VARIANT_TRUE にプロパティを設定すると、SQL Server の OLE DB ドライバーがサーバーにテーブルを作成しようとしたときにエラーが発生します。<br /><br /> SQL Server の OLE DB Driver は DB_S_ERRORSOCCURRED を返します DBPROP_COL_AUTOINCREMENT と DBPROP_COL_NULLABLE 両方が VARIANT_TRUE と*dwOption* DBPROP_COL_NULLABLE がない DBPROPOPTIONS_REQUIRED です。 DBPROP_COL_AUTOINCREMENT と DBPROP_COL_NULLABLE 両方が VARIANT_TRUE の場合、DB_E_ERRORSOCCURRED が返されると、 *dwOption* DBPROP_COL_NULLABLE の dbpropoptions_required します。 列が定義されている、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identity プロパティと、DBPROP_COL_NULLABLE *dwStatus*メンバーが DBPROPSTATUS_CONFLICTING に設定します。|  
|DBPROP_COL_DEFAULT|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明 : 列に対して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の DEFAULT 制約を作成します。<br /><br /> *VValue* DBPROP のメンバーには、さまざまな種類のいずれかを指定できます。 *VValue.vt*メンバーは、列のデータ型と互換性のある型を指定する必要があります。 たとえば、DBTYPE_WSTR で定義された列の既定値として BSTR N/A を定義した場合は互換性の要件が満たされます。 SQL Server の OLE DB ドライバーがサーバーにテーブルを作成しようとしたときにエラーが発生 DBTYPE_R8 として定義された列に同じ既定値を定義します。|  
|DBPROP_COL_DESCRIPTION|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: DBPROP_COL_DESCRIPTION 列プロパティは実装されていません、OLE DB Driver for SQL Server。<br /><br /> *DwStatus*コンシューマーが、プロパティ値を作成しようとすると、DBPROP 構造体のメンバーは DBPROPSTATUS_NOTSUPPORTED を返します。<br /><br /> プロパティの設定要件を満たしません致命的なエラーの OLE DB Driver for SQL Server。 他のすべてのパラメーター値が有効であれば、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のテーブルが作成されます。|  
|DBPROP_COL_FIXEDLENGTH|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE<br /><br /> 説明: SQL Server の OLE DB Driver を使用して DBPROP_COL_FIXEDLENGTH を使用して、コンシューマーが列のデータ型を定義する場合は、データ型のマッピングを決定する、 *wType* DBCOLUMNDESC のメンバーです。 詳細については、次を参照してください。 [ITableDefinition でのデータ型マッピング](../../oledb/ole-db-data-types/data-type-mapping-in-itabledefinition.md)です。|  
|DBPROP_COL_NULLABLE|R/W 読み取り/書き込み<br /><br /> 既定: なし<br /><br /> 説明: テーブルを作成するときに、OLE DB Driver for SQL Server を示すプロパティが設定されている場合に、列が null 値を受け入れるかどうか。 このプロパティが設定されていないときは、列が値として NULL を許容するかどうかは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の既定のデータベース オプション ANSI_NULLS によって決まります。<br /><br /> SQL Server の OLE DB Driver は、ISO 準拠のプロバイダーです。 接続されたセッションでは、ISO 準拠の動作が行われます。 DBPROP_COL_NULLABLE を設定しないと、列は NULL 値を許容します。|  
|DBPROP_COL_PRIMARYKEY|R/W 読み取り/書き込み<br /><br /> 既定値: VARIANT_FALSE 明: VARIANT_TRUE のときに、SQL Server の OLE DB Driver 列を作成、PRIMARY KEY 制約。<br /><br /> 列プロパティとして定義するときは、1 つの列だけが制約を判断できます。 プロパティを VARIANT_TRUE に設定を超える場合、OLE DB Driver for SQL Server が作成しようとすると、1 つの列でエラーが返されます、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブル。<br /><br /> 注: コンシューマーが使用できる**iindexdefinition::createindex**を 2 つ以上の列に PRIMARY KEY 制約を作成します。<br /><br /> DBPROP_COL_PRIMARYKEY と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE のときに、OLE DB Driver for SQL Server は DB_S_ERRORSOCCURRED を返しますと*dwOption* DBPROP_COL_UNIQUE を利用する DBPROPOPTIONS_REQUIRED はありません。<br /><br /> DBPROP_COL_PRIMARYKEY と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE の場合、DB_E_ERRORSOCCURRED が返されると、 *dwOption* DBPROP_COL_UNIQUE の dbpropoptions_required します。 列が定義されている、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identity プロパティと、DBPROP_COL_PRIMARYKEY *dwStatus*メンバーが DBPROPSTATUS_CONFLICTING に設定します。<br /><br /> DBPROP_COL_PRIMARYKEY と DBPROP_COL_NULLABLE 両方が VARIANT_TRUE のときに、SQL Server の OLE DB Driver は、エラーを返します。<br /><br /> SQL Server の OLE DB Driver はからエラーを返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]コンシューマーが無効の列に PRIMARY KEY 制約を作成しようとしたときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型。 作成される列に PRIMARY KEY 制約を定義することはできません、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型**ビット**、**テキスト**、 **ntext**、および**イメージ**です。|  
|DBPROP_COL_UNIQUE|R/W 読み取り/書き込み<br /><br /> 既定値 : VARIANT_FALSE&lt;br&gt;&lt;/br&gt;説明 : 列に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の UNIQUE 制約を適用します。<br /><br /> 列プロパティとして定義するときは、1 つの列だけに制約が適用されます。 コンシューマーが使用できる**iindexdefinition::createindex**を 2 つ以上の列の値の組み合わせに一意の制約を適用します。<br /><br /> SQL Server の OLE DB Driver は DB_S_ERRORSOCCURRED を返します DBPROP_COL_PRIMARYKEY と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE と*dwOption* DBPROPOPTIONS_REQUIRED ではありません。<br /><br /> DBPROP_COL_PRIMARYKEY と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE の場合、DB_E_ERRORSOCCURRED が返されると*dwOption* dbpropoptions_required です。 列が定義されている、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identity プロパティと、DBPROP_COL_PRIMARYKEY *dwStatus*メンバーが DBPROPSTATUS_CONFLICTING に設定します。<br /><br /> SQL Server の OLE DB Driver は DB_S_ERRORSOCCURRED を返します DBPROP_COL_NULLABLE と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE と*dwOption* DBPROPOPTIONS_REQUIRED ではありません。<br /><br /> DBPROP_COL_NULLABLE と DBPROP_COL_UNIQUE 両方が VARIANT_TRUE の場合、DB_E_ERRORSOCCURRED が返されると*dwOption* dbpropoptions_required です。 列が定義されている、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] identity プロパティと、DBPROP_COL_NULLABLE *dwStatus*メンバーが DBPROPSTATUS_CONFLICTING に設定します。<br /><br /> SQL Server の OLE DB Driver はからエラーを返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]コンシューマーが無効の列に UNIQUE 制約を作成しようとしたときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データ型。 作成される列に UNIQUE 制約を定義することはできません、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **ビット**データ型。|  
  
 コンシューマーを呼び出すと**itabledefinition::createtable**、SQL Server の OLE DB Driver はテーブルのプロパティを次のように解釈します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_TBL_TEMPTABLE|R/W 読み取り/書き込み<br /><br /> 既定値: VARIANT_FALSE の説明: 既定では、SQL Server の OLE DB Driver がコンシューマーによってという名前のテーブルを作成します。 ときに VARIANT_TRUE で、OLE DB Driver for SQL Server は、コンシューマー向けに一時テーブル名を生成します。 コンシューマー セット、 *pTableID*のパラメーター **CreateTable**を NULL にします。 *PpTableID*パラメーターは、有効なポインターを含める必要があります。|  
  
 コンシューマーは、正常に作成されたテーブルの行セットが開かれることを要求している場合、OLE DB Driver for SQL Server は、カーソルでサポートされている行セットを開きます。 渡されるプロパティ セットで任意の行セット プロパティを指定できます。  
  
 次の例では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] テーブルを作成します。  
  
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
 [テーブルとパーティション インデックス](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
