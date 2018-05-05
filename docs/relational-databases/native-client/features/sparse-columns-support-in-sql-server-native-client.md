---
title: SQL Server Native Client におけるスパース列のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|features
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sparse columns, ODBC
- sparse columns, SQL Server Native Client
- sparse columns, OLE DB
ms.assetid: aee5ed81-7e23-42e4-92d3-2da7844d9bc3
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 5f9cf56b4ee1a7e3108607912ecba9a05d0815e4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sparse-columns-support-in-sql-server-native-client"></a>SQL Server Native Client におけるスパース列のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はスパース列をサポートしています。 スパース列の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[スパース列を使用する](../../../relational-databases/tables/use-sparse-columns.md)と[列セットの使用](../../../relational-databases/tables/use-column-sets.md)です。  
  
 スパース列の詳細についてでサポート[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client を参照してください[スパース列をサポート&#40;ODBC&#41; ](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)と[スパース列をサポート&#40;OLE DB&#41; ](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md).  
  
 この機能を説明するサンプル アプリケーションについては、次を参照してください。 [SQL Server データ プログラミング サンプル](http://msftdpprodsamples.codeplex.com/)です。  
  
## <a name="user-scenarios-for-sparse-columns-and-sql-server-native-client"></a>スパース列と SQL Server Native Client のユーザー シナリオ  
 スパース列を使用する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ユーザーの一般的なユーザー シナリオの概要を次の表に示します。  
  
|Scenario|動作|  
|--------------|--------------|  
|**選択\*テーブルから**または iopenrowset::openrowset です。|スパースのメンバーではないすべての列が返されます**column_set**、XML 列、スパースのメンバーであるすべての null 以外の列の値を含む**column_set**です。|  
|名前で列を参照する。|スパース列かに関係なく、列を参照できるまたは**column_set**メンバーシップです。|  
|アクセス**column_set**メンバー列計算された XML 列から。|列、スパースのメンバーである**column_set**を選択してアクセスできる、 **column_set**名前によって値が挿入され、内の XML を更新することで更新ができ、 **column_set**列です。<br /><br /> 用のスキーマに従う必要があります値**column_set**列です。|  
|SQLColumns を NULL または '%' (ODBC); の列検索パターンでのテーブルのすべての列のメタデータを取得します。または列を制限しない (OLE DB) と DBSCHEMA_COLUMNS スキーマ行セットを使用します。|メンバーではないすべての列に行を返します、 **column_set**です。 テーブルにスパース**column_set**、その行が返されます。<br /><br /> これを返さないことのメンバーである列のメタデータに注意してください、 **column_set**です。|  
|スパースかどうか、またはメンバーシップに関係なく、すべての列のメタデータを取得、 **column_set**です。 この場合、大量の行が返される可能性があります。|記述子フィールド SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_EXTENDED および呼び出しに設定[SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) (ODBC)。<br /><br /> DBSCHEMA_COLUMNS_EXTENDED スキーマ行セット (OLE DB) idbschemarowset::getrowset を呼び出します。<br /><br /> このシナリオは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のリリースの [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client を使用するアプリケーションでは使用できません。 ただし、このようなアプリケーションでは、システム ビューを直接クエリする可能性があります。|  
|メンバーである列についてのみメタデータを取得、 **column_set**です。 この場合、大量の行が返される可能性があります。|記述子フィールド SQL_SOPT_SS_NAME_SCOPE を SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET に設定し、SQLColumns (ODBC) を呼び出します。<br /><br /> DBSCHEMA_SPARSE_COLUMN_SET スキーマ行セット (OLE DB) idbschemarowset::getrowset を呼び出します。<br /><br /> このシナリオは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のリリースの [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client を使用するアプリケーションでは使用できません。 ただし、そのようなアプリケーションでは、システム ビューに対してクエリを実行できます。|  
|列がスパース列かどうかを確認する。|SQLColumns 結果セット (ODBC) の SS_IS_SPARSE 列を参照してください。<br /><br /> DBSCHEMA_COLUMNS スキーマ行セットの SS_IS_SPARSE 列を調べます (OLE DB)。<br /><br /> このシナリオは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のリリースの [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client を使用するアプリケーションでは使用できません。 ただし、そのようなアプリケーションでは、システム ビューに対してクエリを実行できます。|  
|かどうか、列、 **column_set**です。|SQLColumns の結果セットの SS_IS_COLUMN_SET 列を参照してください。 または、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の列属性である SQL_CA_SS_IS_COLUMN_SET を調べます (ODBC)。<br /><br /> DBSCHEMA_COLUMNS スキーマ行セットの SS_IS_COLUMN_SET 列を調べます。 またはを参照してください*dwFlags* icolumnsinfo::getcolumninfo または DBCOLUMNFLAGS によって icolumnsrowset::getcolumnsrowset によって返される行セットで返されます。 **Column_set**列、DBCOLUMNFLAGS_SS_ISCOLUMNSET が設定されます (OLE DB)。<br /><br /> このシナリオは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] より前のリリースの [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] Native Client を使用するアプリケーションでは使用できません。 ただし、そのようなアプリケーションでは、システム ビューに対してクエリを実行できます。|  
|含まないテーブルに対して BCP でスパース列のインポートとエクスポート**column_set**です。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の以前のバージョンから動作は変更されていません。|  
|含むテーブルに対して BCP でスパース列のインポートとエクスポート、 **column_set**です。|**Column_set**がインポートされ、XML; と同じ方法でエクスポートは、として**varbinary (max)** 場合としてまたはバイナリ型としてバインドされている**nvarchar (max)** 場合、としてバインド**char**または**wchar**型です。<br /><br /> 列、スパースのメンバーである**column_set**個別の列としてはエクスポートされませんの値にのみエクスポートされている、 **column_set**です。|  
|**queryout** BCP の動作です。|明示的に指定された列の処理は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の以前のバージョンから変更されていません。<br /><br /> スキーマが異なる列の間のインポートおよびエクスポートを含むシナリオでは、特別な処理が必要になる場合があります。<br /><br /> BCP の詳細については、後の「一括コピー (BCP) によるスパース列のサポート」を参照してください。|  
  
## <a name="down-level-client-behavior"></a>下位クライアントの動作  
 ダウンレベルのクライアントは、スパースのメンバーではない列についてのみメタデータを返します**column_set** SQLColumns および DBSCHMA_COLUMNS です。 導入された追加の OLE DB スキーマ行セット[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]Native Client が使用できないことも、SQL_SOPT_SS_NAME_SCOPE を使用して ODBC の SQLColumns に変更されます。  
  
 ダウンレベルのクライアントが、スパースのメンバーである列にアクセスできる**column_set**名前で、 **column_set**列で使用できるために XML 列として[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]クライアント。  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>一括コピー (BCP) によるスパース列のサポート  
 スパース列の ODBC または OLE DB の BCP API への変更がないか、 **column_set**機能します。  
  
 テーブルがある場合、 **column_set**、スパース列は個別の列として処理されません。 値にすべてのスパース列の値が含まれている、 **column_set**、XML 列と同じ方法でエクスポートするは、として**varbinary (max)** 場合としてまたはバイナリ型としてバインドされている**nvarchar (max)** 場合としてバインドされている、 **char**または**wchar**型)。 インポート時に、 **column_set**値は、のスキーマに準拠している必要があります、 **column_set**です。  
  
 **Queryout**操作を明示的に参照されている列の処理方法に変更はありません。 **column_set**列が XML 列と同じ動作があるし、スパースかどうかも何も起こりませんの取り扱いをスパース列をという名前です。  
  
 ただし場合、 **queryout**使用は、スパース列セットを名前のメンバーであるスパース列を参照するは、エクスポートしてには、同じ構造のテーブルに直接インポートを行うことはできません。 これは、BCP と一貫したメタデータを使用するため、**選択\***  、インポート操作に一致するようになって、 **column_set**このメタデータを持つメンバーの列です。 インポートする**column_set**メンバーの列の個別に、目的が参照するテーブルのビューを定義する必要があります**column_set**列、およびするが、ビューを使用してインポート操作を実行する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client プログラミング](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
