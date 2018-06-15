---
title: XML データ型の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|features
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetChange interface
- IRowsetUpdate interface
- data access [SQL Server Native Client], xml data type
- SQL Server Native Client OLE DB schema rowsets
- PROVIDER_TYPES rowset
- IColumnsInfo interface
- IRowsetFind interface
- IColumnsRowset interface
- PROCEDURE_PARAMETERS rowset
- SQLNCLI, XML
- xml data type [SQL Server], SQL Server Native Client
- SQL Server Native Client, XML
- IRowset interface
- ISequentialStream interface
- ISSCommandWithParameters interface
- SS_XMLSCHEMA rowset
- SQL Server Native Client OLE DB interfaces
- XML [SQL Server], SQL Server Native Client
- COLUMNS rowset
ms.assetid: a7af5b72-c5c2-418d-a636-ae4ac6270ee5
caps.latest.revision: 44
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e3d2cf487958f09af1825456f605a9f73a44e27e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32957497"
---
# <a name="using-xml-data-types"></a>XML データ型の使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]導入された、 **xml**データ型を XML ドキュメントを保存することができ、フラグメント、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。 **Xml**データ型は、組み込みのデータ型で[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]などの他の組み込み型のようないくつかの方法であると**int**と**varchar**です。 他の組み込み型にも使用できるように、 **xml**データ型のテーブルの作成時に列型として以外の場合は、変数の型、パラメーターの型、または関数の戻り値型であるとして、または CAST や CONVERT 関数でします。  
  
## <a name="programming-considerations"></a>プログラミングの考慮事項  
 XML は自己記述型で、必要に応じて、次のようにドキュメントのエンコードを指定する XML ヘッダーを含めることができます。  
  
 `<?xml version="1.0" encoding="windows-1252"?><doc/>`  
  
 XML 標準では、ドキュメントの先頭の数バイトを調べることで、ドキュメントで使用しているエンコードを XML プロセッサで検出する方法が説明されています。 アプリケーションで指定するエンコードとドキュメントで指定されているエンコードが競合する場合があります。 バインドされたパラメーターとして渡されるドキュメントの場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では XML がバイナリ データとして扱われるので、データ変換は行われず、XML パーサーはドキュメントに指定されたエンコードを問題なく使用することができます。 ただし、WSTR としてバインドされた XML データの場合、そのドキュメントが Unicode でエンコードされていることをアプリケーションで確認する必要があります。 この場合、必然的にドキュメントが DOM に読み込まれることになり、エンコードが Unicode に変更され、ドキュメントはシリアル化されます。 この処理が行われないと、データ変換が行われ、結果として無効なまたは破損した XML になります。  
  
 また、XML がリテラルで指定された場合も競合が発生する可能性があります。 たとえば、次に示すステートメントは無効です。  
  
 `INSERT INTO xmltable(xmlcol) VALUES('<?xml version="1.0" encoding="UTF-16"?><doc/>')`  
  
 `INSERT INTO xmltable(xmlcol) VALUES(N'<?xml version="1.0" encoding="UTF-8"?><doc/>')`  
  
## <a name="sql-server-native-client-ole-db-provider"></a>SQL Server Native Client OLE DB プロバイダー  
 DBTYPE_XML は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの新しい XML 固有のデータ型です。 また、既存の OLE DB 型である DBTYPE_BYTES、DBTYPE_WSTR、DBTYPE_BSTR、DBTYPE_XML、DBTYPE_STR、DBTYPE_VARIANT、および DBTYPE_IUNKNOWN を使用して、XML データにアクセスできます。 XML 型の列に格納されたデータ型は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの行セット内の列から、次の形式で取得できます。  
  
-   テキスト文字列  
  
-   **ISequentialStream**  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、SAX リーダーは含まれませんが、 **ISequentialStream** MSXML SAX、DOM オブジェクトに簡単に渡すことができます。  
  
 **ISequentialStream**大きな XML ドキュメントの取得のために使用する必要があります。 他の大きな値の型で使用される方法と同じ方法を XML でも使用できます。 詳細については、次を参照してください。[大きな値の型を使用して](../../../relational-databases/native-client/features/using-large-value-types.md)です。  
  
 行セットの XML も取得できます、型の列に格納されているデータの挿入、またはなどの通常のインターフェイスを使用して、アプリケーションによって更新された**irow::getcolumns**、 **irowchange:**、および**icommand::execute**です。 同様に取得する場合、アプリケーション プログラム渡すことができますか、テキスト文字列または**ISequentialStream**を[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーです。  
  
> [!NOTE]  
>  文字列形式で XML データを送信する、 **ISequentialStream**インターフェイスを取得する必要あります**ISequentialStream** DBTYPE_IUNKNOWN を指定して、設定をその*pObject*バインドで null に渡す引数。  
  
 コンシューマーのバッファーが小さすぎて取得した XML データが切り捨てられるときは、データ長が 0xffffffff で返されます。この値は、長さが不明であることを意味します。 この動作は、実際のデータの前に長さの情報を送信しないでクライアントにストリーム送信されるデータ型の実装と一貫性を持たせています。 場合によっては、実際の長さは、プロバイダーがなど、値全体をバッファーがときに返される**irowset::getdata**データ変換を行うとします。  
  
 SQL Server に送信される XML データは、サーバーではバイナリ データとして扱われます。 その結果、変換が行われず、XML パーサーが XML エンコードを自動検出できます。 これにより、広範な XML ドキュメント (UTF-8 でエンコードされた XML ドキュメントなど) を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] への入力として受け取ることができます。  
  
 入力 XML が DBTYPE_WSTR にバインドされる場合、不要なデータ変換によってデータが破損しないようにするために、アプリケーションでは入力 XML が Unicode でエンコードされていることを確認する必要があります。  
  
### <a name="data-bindings-and-coercions"></a>データ バインドと強制型変換  
 次の表は、バインドおよび強制型はリストされているデータを使用するときに発生する、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **xml**データ型。  
  
|データ型|SQL Server の<br /><br /> **XML**|SQL Server の<br /><br /> **非 XML**|サーバーから<br /><br /> **XML**|サーバーから<br /><br /> **非 XML**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_XML|パススルー<sup>6、7</sup>|エラー<sup>1</sup>|[OK]<sup>11、6</sup>|エラー<sup>8</sup>|  
|DBTYPE_BYTES|パススルー<sup>6、7</sup>|N/A<sup>2</sup>|[OK] <sup>11、6</sup>|N/A <sup>2</sup>|  
|DBTYPE_WSTR|パススルー<sup>6、10</sup>|N/A <sup>2</sup>|[OK]<sup>4、6、12</sup>|N/A <sup>2</sup>|  
|DBTYPE_BSTR|パススルー<sup>6、10</sup>|N/A <sup>2</sup>|OK <sup>3</sup>|N/A <sup>2</sup>|  
|DBTYPE_STR|[OK]<sup>6、9、10</sup>|N/A <sup>2</sup>|[OK]<sup>5、6、12</sup>|N/A <sup>2</sup>|  
|DBTYPE_IUNKNOWN|経由のバイト ストリーム**ISequentialStream**<sup>7</sup>|N/A <sup>2</sup>|経由のバイト ストリーム**ISequentialStream**<sup>11</sup>|N/A <sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|パススルー<sup>6、7</sup>|N/A <sup>2</sup>|なし|N/A <sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|パススルー<sup>6、10</sup>|N/A <sup>2</sup>|OK<sup>3</sup>|N/A <sup>2</sup>|  
  
 <sup>1</sup>サーバー以外の型に dbtype_xml 型が指定された場合**icommandwithparameters::setparameterinfo**アクセサーの型が dbtype_xml 型、およびステートメントが実行されたときにエラーが発生した (DB_E_ERRORSOCCURRED、パラメーターの状態は dbstatus_e_badaccessor になります)。 データを、サーバーに送信するそれ以外の場合は、サーバーには、XML からパラメーターのデータ型への暗黙的な変換がないことを示すエラーが返されます。  
  
 <sup>2</sup>このトピックの範囲を超えています。  
  
 <sup>3</sup>形式は utf-16、ありません bye 順マーク (BOM)、エンコード仕様、終端の null はありません。  
  
 <sup>4</sup>形式は utf-16 BOM なし、ありませんエンコード仕様、終端の null です。  
  
 <sup>5</sup>マルチバイト文字列が null で終端のクライアント コード ページでエンコードされた形式です。 Unicode を使用できるサーバーから変換するとデータが破損する場合があるので、このバインドはお勧めしません。  
  
 <sup>6</sup>BY_REF を使用できます。  
  
 <sup>7</sup>utf-16 データは BOM で始まる必要があります。 BOM で始まらない場合は、サーバーでエンコードが正しく認識されないことがあります。  
  
 <sup>8</sup>アクセサーの作成時、またはフェッチ時に検証が行われます。 エラーは DB_E_ERRORSOCCURRED です。その場合、バインドの状態は DBBINDSTATUS_UNSUPPORTEDCONVERSION に設定されます。  
  
 <sup>9</sup>データは、サーバーに送信される前にクライアントのコード ページを使用して Unicode に変換します。 ドキュメントのエンコードがクライアントのコード ページと一致しない場合、変換によってデータが破損することがあるので、このバインドはお勧めしません。  
  
 <sup>10</sup>BOM は常に、サーバーに送信されるデータに追加します。 既にデータが BOM で始まる場合、この動作により、バッファーの先頭に 2 つの BOM が存在することになります。 サーバーは、utf-16 としてエンコードを認識する最初の BOM を使用し、し、それを破棄します。 2 つ目の BOM は、幅が 0 の改行を行わない空白文字として解釈されます。  
  
 <sup>11</sup>形式は utf-16 エンコード仕様、BOM が追加、サーバーから受け取ったデータにします。 空の文字列が、サーバーによって返される場合は、アプリケーションに BOM が返されます。 バッファーの長さがバイト単位の数が奇数の場合は、データが適切に切り捨てられます。 値全体がチャンク単位で返される場合は、適切な値を再構成する連結できます。  
  
 <sup>12</sup>オーバーフロー エラーが報告された場合は、バッファーの長さが 2 より小さい文字である、終端の null--の領域が不足します。  
  
> [!NOTE]  
>  NULL の XML 値の場合は、データは返されません。  
  
 XML 標準では、UTF-16 でエンコードされた XML をバイト順マーク (BOM) で始める必要があります。BOM は UTF-16 の文字コードでは 0xFEFF です。 WSTR および BSTR バインドを使用するときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client が必要とまたはバインドによってエンコードが暗黙的に BOM を追加していません。 BYTES バインド、XML バインド、または IUNKNOWN バインドを使用する場合、その目的は他の XML プロセッサや XML ストレージ システムでの処理を簡単にすることです。 この場合、BOM は UTF-16 でエンコードされた XML を示し、SQL Server を含め XML プロセッサの多くは値の先頭の数バイトを調べてエンコードを推定するので、アプリケーションで実際のエンコードを考慮する必要はありません。 XML データから受信した[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client バイト、XML、または IUNKNOWN を使用するバインディングは、常にでエンコードされた utf-16 BOM とエンコード宣言は埋め込まれません。  
  
 OLE DB core services で提供されるデータ変換 (**IDataConvert**) dbtype_xml 型には適用されません。  
  
 検証はデータがサーバーに送信されたときに行われます。 クライアント側の検証とエンコードの変更はアプリケーションで処理する必要がありますが、直接処理するのではなく、DOM リーダーや SAX リーダーを使用して XML データを処理することを強くお勧めします。  
  
 DBTYPE_ と DBTYPE_EMPTY は入力パラメーターは出力パラメーターや結果にバインドできます。 入力パラメーターにバインドした場合、状態を DBSTATUS_S_ISNULL または DBSTATUS_S_DEFAULT に設定する必要があります。  
  
 DBTYPE_XML は DBTYPE_EMPTY および DBTYPE_NULL に変換でき、DBTYPE_EMPTY は DBTYPE_XML に変換できますが、DBTYPE_NULL を DBTYPE_XML に変換することはできません。 この動作は、DBTYPE_WSTR と一貫性があります。  
  
 DBTYPE_IUNKNOWN は上記の表に示したようにサポート済みのバインドですが、DBTYPE_XML と DBTYPE_IUNKNOWN との間では変換は行われません。 DBTYPE_IUNKNOWN は、DBTYPE_BYREF と共に使用することはできません。  
  
### <a name="ole-db-rowset-additions-and-changes"></a>OLE DB 行セットに関する追加事項と変更事項  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client では、新しい値が追加または多くの主要な OLE DB スキーマ行セットを変更します。  
  
#### <a name="the-columns-and-procedureparameters-schema-rowsets"></a>COLUMNS スキーマ行セットと PARAMETERS スキーマ行セット  
 COLUMNS スキーマ行セットと PROCEDURE_PARAMETERS スキーマ行セットに次の列が追加されました。  
  
|列名|型|Description|  
|-----------------|----------|-----------------|  
|SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|XML スキーマ コレクションを定義しているカタログの名前。 XML 型以外の列または型指定されていない XML 列の場合は NULL です。|  
|SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|XML スキーマ コレクションを定義しているスキーマの名前。 XML 型以外の列または型指定されていない XML 列の場合は NULL です。|  
|SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|XML スキーマ コレクションの名前。 XML 型以外の列または型指定されていない XML 列の場合は NULL です。|  
  
#### <a name="the-providertypes-schema-rowset"></a>PROVIDER_TYPES スキーマ行セット  
 PROVIDER_TYPES スキーマ行セットに、COLUMN_SIZE の値は 0 を**xml**データ型、DATA_TYPE は DBTYPE_XML です。  
  
#### <a name="the-ssxmlschema-schema-rowset"></a>SS_XMLSCHEMA スキーマ行セット  
 クライアントで XML スキーマ情報を取得できるように、新しいスキーマ行セット SS_XMLSCHEMA が導入されました。 SS_XMLSCHEMA 行セットには、次の列が含まれています。  
  
|列名|型|Description|  
|-----------------|----------|-----------------|  
|SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|XML コレクションが属するカタログ。|  
|SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|XML コレクションが属するスキーマ。|  
|SCHEMACOLLECTIONNAME|DBTYPE_WSTR|型指定された XML 列の場合は、XML スキーマ コレクション NULL それ以外の場合の名前。|  
|TARGETNAMESPACEURI|DBTYPE_WSTR|XML スキーマの対象名前空間。|  
|SCHEMACONTENT|DBTYPE_WSTR|XML スキーマのコンテンツ。|  
  
 各 XML スキーマのスコープは、カタログ名、スキーマ名、スキーマ コレクション名、および対象名前空間を識別する Uniform Resource Identifier (URI) 別に設定されます。 また、DBSCHEMA_XML_COLLECTIONS という名前の新しい GUID も定義されます。 SS_XMLSCHEMA スキーマ行セットの制限数と制限列は、次のように定義されます。  
  
|GUID|制限数|制限列|  
|----------|----------------------------|------------------------|  
|DBSCHEMA_XML_COLLECTIONS|4|SCHEMACOLLECTION_CATALOGNAME<br /><br /> SCHEMACOLLECTION_SCHEMANAME<br /><br /> SCHEMACOLLECTIONNAME<br /><br /> TARGETNAMESPACEURI|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>OLE DB プロパティ セットに関する追加事項と変更事項  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、新しい値を追加またはに多くの主要な OLE DB プロパティのセットを変更します。  
  
#### <a name="the-dbpropsetsqlserverparameter-property-set"></a>DBPROPSET_SQLSERVERPARAMETER プロパティ セット  
 サポートするために、 **xml** OLE DB 経由でデータ型[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、次の値を含む新しい DBPROPSET_SQLSERVERPARAMETER プロパティ セットを実装します。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|XML スキーマ コレクションを定義しているカタログ (データベース) の名前。 SQL の 3 部構成の名前識別子の一部です。|  
|SSPROP_PARAM_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|スキーマ コレクションに含まれている XML スキーマの名前。 SQL の 3 部構成による名前の識別子の一部になります。|  
|SSPROP_PARAM_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|カタログに含まれている XML スキーマ コレクションの名前。SQL の 3 部構成による名前の識別子の一部になります。|  
  
#### <a name="the-dbpropsetsqlservercolumn-property-set"></a>DBPROPSET_SQLSERVERCOLUMN プロパティ セット  
 内のテーブルの作成をサポートする、 **ITableDefinition**インターフェイス、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、DBPROPSET_SQLSERVERCOLUMN プロパティ セットに 3 つの新しい列を追加します。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME|VT_BSTR|型指定された XML 列の場合、このプロパティは XML スキーマが格納されているカタログ名を指定する文字列です。 他のデータ型の列の場合、このプロパティでは空文字列が返されます。|  
|SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME|VT_BSTR|型指定された XML 列の場合、このプロパティはこの列を定義している XML スキーマ名を指定する文字列です。|  
|SSPROP_COL_XML_SCHEMACOLLECTIONNAME|VT_BSTR|型指定された XML 列の場合、このプロパティは値を定義している XML スキーマ コレクション名を指定する文字列です。|  
  
 SSPROP_PARAM 値と同様に、これらのプロパティはすべて省略可能なプロパティで、既定値は空です。 SSPROP_COL_XML_SCHEMACOLLECTION_CATALOGNAME と SSPROP_COL_XML_SCHEMACOLLECTION_SCHEMANAME は、SSPROP_COL_XML_SCHEMACOLLECTIONNAME が指定されている場合のみ指定できます。 XML をサーバーに渡すときにこれらの値が含まれていると、これらの値が妥当かどうかが現在のデータベースとの比較によりチェックされ、インスタンス データがスキーマとの比較によりチェックされます。 どの場合でも、これらはすべて空かすべて設定されている場合に妥当と判断されます。  
  
### <a name="ole-db-interface-additions-and-changes"></a>OLE DB インターフェイスに関する追加事項と変更事項  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client では、新しい値が追加または多くの主要な OLE DB インターフェイスを変更します。  
  
#### <a name="the-isscommandwithparameters-interface"></a>ISSCommandWithParameters インターフェイス  
 サポートするために、 **xml** OLE DB 経由でデータ型[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、多数の変更の追加などを実装して、 [ISSCommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)インターフェイスです。 この新しいインターフェイスが、主要な OLE DB インターフェイスから継承**ICommandWithParameters**です。 継承される 3 つのメソッドだけでなく**ICommandWithParameters**です。**GetParameterInfo**、 **MapParameterNames**、および**SetParameterInfo**です。**ISSCommandWithParameters**提供、 [GetParameterProperties](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-getparameterproperties-ole-db.md)と[SetParameterProperties](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-setparameterproperties-ole-db.md)サーバー固有のデータ型の処理に使用されるメソッド。  
  
> [!NOTE]  
>  **ISSCommandWithParameters**インターフェイスもを使用する、新しい SSPARAMPROPS 構造体。  
  
#### <a name="the-icolumnsrowset-interface"></a>IColumnsRowset インターフェイス  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client は、以下を追加します。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-特定の列によって返される行セットに、 **IColumnRowset::GetColumnsRowset**メソッドです。 これらの列には、XML スキーマ コレクションの 3 部構成の名前が含まれます。 XML 以外の列または型指定されていない XML 列の場合、これら 3 列の既定値はすべて NULL になります。  
  
|列名|型|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_CATALOGNAME|DBTYPE_WSTR|XML スキーマ コレクションが属するカタログ。<br /><br /> それ以外の場合は、NULL です。|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTION_SCHEMANAME|DBTYPE_WSTR|XML スキーマ コレクションが属するスキーマ。 それ以外の場合は、NULL です。|  
|DBCOLUMN_SS_XML_SCHEMACOLLECTIONNAME|DBTYPE_WSTR|型指定された XML 列の場合は、XML スキーマ コレクションの名前です。それ以外の場合は、NULL です。|  
  
#### <a name="the-irowset-interface"></a>IRowset インターフェイス  
 XML 列に XML インスタンスを取得、 **irowset::getdata**メソッドです。 クライアントで指定されているバインドによって異なりますが、XML インスタンスは DBTYPE_BSTR、DBTYPE_WSTR、DBTYPE_VARIANT、DBTYPE_XML、DBTYPE_STR、DBTYPE_BYTES として、または DBTYPE_IUNKNOWN 経由のインターフェイスとして取得できます。 コンシューマーが DBTYPE_BSTR、DBTYPE_WSTR、または DBTYPE_VARIANT を指定すると、プロバイダーで XML インスタンスの型がユーザーが要求した型に変換され、対応するバインドで指定した場所に格納されます。  
  
 コンシューマーが DBTYPE_IUNKNOWN を指定する場合を設定し、 *pObject* NULL の場合、またはセットへの引数、 *pObject*引数に IID_ISequentialStream、プロバイダーを返します、 **ISequentialStream**コンシューマーにインターフェイスのコンシューマーが列の XML データをストリーミングできるようにします。 **ISequentialStream** Unicode 文字のストリームとして XML データを返します。  
  
 プロバイダーは DBTYPE_IUNKNOWN にバインドされた XML 値を返すときに、`sizeof (IUnknown *)` でサイズ値を報告します。 この動作は、列が DBTYPE_IUnknown または DBTYPE_IDISPATCH としてバインドされる場合行われる動作、および正確な列のサイズを特定できない場合に DBTYPE_IUNKNOWN や ISequentialStream で行われる動作と同じです。  
  
#### <a name="the-irowsetchange-interface"></a>IRowsetChange インターフェイス  
 コンシューマーは、列の XML インスタンスを 2 とおりの方法で更新できます。 最初の 1 つは、記憶域オブジェクトを通じて、 **ISequentialStream**プロバイダーによって作成します。 コンシューマーが呼び出すことができます、 **isequentialstream::write**メソッドを直接プロバイダーによって返される XML インスタンスを更新します。  
  
 2 番目の方法では、 **irowsetchange::setdata**または**irowsetchange::insertrow**メソッドです。 この方法では、コンシューマーのバッファーに格納されている XML インスタンスを DBTYPE_BSTR 型、DBTYPE_WSTR 型、DBTYPE_VARIANT 型、DBTYPE_XML 型、または DBTYPE_IUNKNOWN 型のバインドで指定できます。  
  
 DBTYPE_BSTR、DBTYPE_WSTR、または DBTYPE_VARIANT の場合、コンシューマーのバッファーに存在する XML インスタンスがプロバイダーによって適切な列に格納されます。  
  
 DBTYPE_IUNKNOWN と isequentialstream、コンシューマーが任意のストレージ オブジェクトを指定しない場合、コンシューマー作成する必要があります、 **ISequentialStream**オブジェクトをあらかじめし、オブジェクトが、XML ドキュメントをバインドし、オブジェクトを使用して、プロバイダーに渡す、 **irowsetchange::setdata**メソッドです。 コンシューマー作成することも、ストレージ オブジェクト、pObject 引数に IID_ISequentialStream を設定、作成、 **ISequentialStream**オブジェクトを渡す、 **ISequentialStream**オブジェクトを**irowsetchange::setdata**メソッドです。 どちらの場合、プロバイダーが使用して XML オブジェクトを取得できます、 **ISequentialStream**オブジェクトし、適切な列に挿入します。  
  
#### <a name="the-irowsetupdate-interface"></a>IRowsetUpdate インターフェイス  
 **IRowsetUpdate**インターフェイスには、遅延更新のための機能が用意されています。 行セットで使用できるデータがコンシューマー呼び出すまでは他のトランザクションに入手されません、 **IRowsetUpdate:Update**メソッドです。  
  
#### <a name="the-irowsetfind-interface"></a>IRowsetFind インターフェイス  
 **Irowsetfind::findnextrow**メソッドでは機能しません、 **xml**データ型。 ときに**irowsetfind::findnextrow**が呼び出されたと*hAccessor*引数では、DBTYPE_XML の列を指定、DB_E_BADBINDINFO が返されます。 この動作は、検索対象の列の型とは無関係に行われます。 他のバインディング型に対して、 **FindNextRow**検索する列がの場合、db_e_badcompareop を返して失敗した、 **xml**データ型。  
  
## <a name="sql-server-native-client-odbc-driver"></a>SQL Server Native Client ODBC ドライバー  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、変更の数に加えられたさまざまな機能をサポートする、 **xml**データ型。  
  
### <a name="sqlcolattribute"></a>SQLColAttribute  
 [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md)関数には、SQL_CA_SS_XML_SCHEMACOLLECTION_CATALOG_NAME、SQL_CA_SS_XML_SCHEMACOLLECTION_SCHEMA_NAME、sql_ca_ss _XML_SCHEMACOLLECTION_NAME を含む、3 つの新しいフィールド識別子です。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーは、SQL_DESC_DISPLAY_SIZE 列と SQL_DESC_LENGTH 列の SQL_SS_LENGTH_UNLIMITED を報告します。  
  
### <a name="sqlcolumns"></a>SQLColumns  
 [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md)関数には、次の 3 つの新しい列という、SS_XML_SCHEMACOLLECTION_SCHEMA_NAME、および追加されました。 既存の TYPE_NAME 列を使用して XML 型の名前が示されます。XML 型の列または XML 型のパラメーターの DATA_TYPE は SQL_SS_XML になります。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、COLUMN_SIZE と CHAR_OCTET_LENGTH 値として SQL_SS_LENGTH_UNLIMITED を報告します。  
  
### <a name="sqldescribecol"></a>SQLDescribeCol  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]で、列のサイズを特定できない場合は、Native Client ODBC ドライバーは SQL_SS_LENGTH_UNLIMITED を報告、 [SQLDescribeCol](../../../relational-databases/native-client-odbc-api/sqldescribecol.md)関数。  
  
### <a name="sqlgettypeinfo"></a>SQLGetTypeInfo  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、COLUMN_SIZE の最大として SQL_SS_LENGTH_UNLIMITED を報告、 **xml**のデータ型の[SQLGetTypeInfo](../../../relational-databases/native-client-odbc-api/sqlgettypeinfo.md)関数。  
  
### <a name="sqlprocedurecolumns"></a>SQLProcedureColumns  
 [SQLProcedureColumns](../../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md)関数は、同じ列の追加として、 **SQLColumns**関数。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、COLUMN_SIZE の最大として SQL_SS_LENGTH_UNLIMITED を報告、 **xml**データ型。  
  
### <a name="supported-conversions"></a>サポートされる変換  
 SQL データ型から C データ型に変換する際、SQL_C_WCHAR、SQL_C_BINARY、および SQL_C_CHAR は、次の条件下ですべて SQL_SS_XML に変換できます。  
  
-   SQL_C_WCHAR: 形式は UTF-16 で、バイト順マーク (BOM) は付加されず、NULL で終端が示されます。  
  
-   SQL_C_BINARY: 形式は UTF-16 で、NULL で終端は示されません。 サーバーから受け取ったデータに BOM が追加されます。 サーバーから空文字列が返されても、アプリケーションには BOM が返されます。 バッファー長が奇数バイトの場合、データは適切に切り捨てられます。 1 つの値が複数のチャンクで返される場合、それぞれを連結して正しい値を再構成できます。  
  
-   SQL_C_CHAR: クライアント コード ページでエンコードされ、NULL で終端が示される、マルチバイト文字列形式です。 UTF-16 を使用できるサーバーから変換するとデータが破損する場合があるので、このバインドはお勧めしません。  
  
 C データ型から SQL データ型に変換する際、SQL_C_WCHAR、SQL_C_BINARY、および SQL_C_CHAR は、次の条件下ですべて SQL_SS_XML に変換できます。  
  
-   SQL_C_WCHAR: サーバーに送信されるデータには必ず BOM が追加されます。 既にデータが BOM で始まる場合、この動作により、バッファーの先頭に 2 つの BOM が存在することになります。 サーバーでは、1 つ目の BOM からエンコードを UTF-16 と認識した後、その BOM を破棄します。 2 つ目の BOM は、幅が 0 の改行を行わない空白文字として解釈されます。  
  
-   SQL_C_BINARY: 変換が行われないので、データはそのままの状態でサーバーに渡されます。 UTF-16 データは BOM で始まる必要があります。BOM で始まらない場合、エンコードがサーバーで適切に認識されません。  
  
-   SQL_C_CHAR: データはクライアント上で UTF-16 に変換され、サーバーにそのまま SQL_C_WCHAR として送信されます (ただし、BOM が追加されます)。 XML がクライアントのコード ページでエンコードされない場合、この変換が原因でデータが破損することがあります。  
  
 XML 標準では、UTF-16 でエンコードされた XML をバイト順マーク (BOM) で始める必要があります。BOM は UTF-16 の文字コードでは 0xFEFF です。 SQL_C_BINARY バインドを使用するときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client が必要とまたはように、バインドによってエンコードが暗黙的に、BOM を追加していません。 SQL_C_BINARY バインドを使用する目的は、その他の XML プロセッサや XML ストレージ システムでの処理を簡単にすることです。 この場合、BOM は UTF-16 でエンコードされた XML を示し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を含め XML プロセッサの多くは値の先頭の数バイトを調べてエンコードを推定するので、アプリケーションで実際のエンコードを考慮する必要はありません。 XML データから受信した[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client SQL_C_BINARY を使用するバインディングは、常にでエンコードされた utf-16 BOM とエンコード宣言は埋め込まれません。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [ISSCommandWithParameters (&) #40";"OLE DB"&"#41;](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
