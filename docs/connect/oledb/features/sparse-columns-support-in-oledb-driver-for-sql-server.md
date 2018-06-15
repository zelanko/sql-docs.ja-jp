---
title: SQL Server の OLE DB ドライバーのスパース列のサポート |Microsoft ドキュメント
description: スパース列が SQL Server の OLE DB Driver のサポートします。
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sparse columns, OLE DB Driver for SQL Server
- sparse columns, OLE DB
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d8e0139f126760cd62b44d699d8a0eef4fbaee38
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612008"
---
# <a name="sparse-columns-support-in-ole-db-driver-for-sql-server"></a>SQL Server の OLE DB ドライバーのスパース列のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server には、スパース列がサポートしています。 スパース列の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[スパース列を使用する](../../../relational-databases/tables/use-sparse-columns.md)と[列セットの使用](../../../relational-databases/tables/use-column-sets.md)です。  
  
 SQL Server の OLE DB ドライバーでスパース列のサポートの詳細については[スパース列をサポート&#40;OLE DB&#41;](../../oledb/ole-db/sparse-columns-support-ole-db.md)です。  
  
 この機能を説明するサンプル アプリケーションについては、次を参照してください。 [SQL Server データ プログラミング サンプル](http://msftdpprodsamples.codeplex.com/)です。  
  
## <a name="user-scenarios-for-sparse-columns-and-ole-db-driver-for-sql-server"></a>スパース列および OLE DB Driver for SQL Server のユーザー シナリオ  
 次の表は、スパース列を含む SQL Server ユーザーの OLE DB Driver 用の一般的なユーザー シナリオを示します。  
  
|シナリオ|動作|  
|--------------|--------------|  
|**選択\*テーブルから**または iopenrowset::openrowset です。|スパースのメンバーではないすべての列が返されます**column_set**、XML 列、スパースのメンバーであるすべての null 以外の列の値を含む**column_set**です。|  
|名前で列を参照する。|スパース列かに関係なく、列を参照できるまたは**column_set**メンバーシップです。|  
|アクセス**column_set**メンバー列計算された XML 列から。|列、スパースのメンバーである**column_set**を選択してアクセスできる、 **column_set**名前によって値が挿入され、内の XML を更新することで更新ができ、 **column_set**列です。<br /><br /> 用のスキーマに従う必要があります値**column_set**列です。|  
|DBSCHEMA_COLUMNS スキーマ行セット、テーブルの列を制限しない (OLE DB) でのすべての列のメタデータを取得します。|メンバーではないすべての列に行を返します、 **column_set**です。 テーブルにスパース**column_set**、その行が返されます。<br /><br /> これを返さないことのメンバーである列のメタデータに注意してください、 **column_set**です。|  
|スパースかどうか、またはメンバーシップに関係なく、すべての列のメタデータを取得、 **column_set**です。 この場合、大量の行が返される可能性があります。|DBSCHEMA_COLUMNS_EXTENDED スキーマ行セットの idbschemarowset::getrowset を呼び出します。|  
|メンバーである列についてのみメタデータを取得、 **column_set**です。 この場合、大量の行が返される可能性があります。|DBSCHEMA_SPARSE_COLUMN_SET スキーマ行セットの idbschemarowset::getrowset を呼び出します。|  
|列がスパース列かどうかを確認する。|DBSCHEMA_COLUMNS スキーマ行セットの SS_IS_SPARSE 列を調べます (OLE DB)。|  
|かどうか、列、 **column_set**です。|DBSCHEMA_COLUMNS スキーマ行セットの SS_IS_COLUMN_SET 列を調べます。 またはを参照してください*dwFlags* icolumnsinfo::getcolumninfo または DBCOLUMNFLAGS によって icolumnsrowset::getcolumnsrowset によって返される行セットで返されます。 **Column_set**列、DBCOLUMNFLAGS_SS_ISCOLUMNSET が設定されます。|  
|含まないテーブルに対して BCP でスパース列のインポートとエクスポート**column_set**です。|SQL Server の以前のバージョンの OLE DB ドライバーからの動作の変更です。|  
|含むテーブルに対して BCP でスパース列のインポートとエクスポート、 **column_set**です。|**Column_set**がインポートされ、XML; と同じ方法でエクスポートは、として**varbinary (max)** 場合としてまたはバイナリ型としてバインドされている**nvarchar (max)** 場合、としてバインド**char**または**wchar**型です。<br /><br /> 列、スパースのメンバーである**column_set**個別の列としてはエクスポートされませんの値にのみエクスポートされている、 **column_set**です。|  
|**queryout** BCP の動作です。|SQL Server の以前のバージョンの OLE DB ドライバーから明示的に指定された列の処理は、変更はありません。<br /><br /> スキーマが異なる列の間のインポートおよびエクスポートを含むシナリオでは、特別な処理が必要になる場合があります。<br /><br /> BCP の詳細については、後の「一括コピー (BCP) によるスパース列のサポート」を参照してください。|  
  
## <a name="down-level-client-behavior"></a>下位クライアントの動作  
 ダウンレベルのクライアントは、スパースのメンバーではない列についてのみメタデータを返します**column_set** SQLColumns および DBSCHMA_COLUMNS です。
  
 ダウンレベルのクライアントが、スパースのメンバーである列にアクセスできる**column_set**名前で、 **column_set**列で使用できるために XML 列として[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]クライアント。  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>一括コピー (BCP) によるスパース列のサポート  
 スパース列の OLE DB の BCP API への変更がないか、 **column_set**機能します。  
  
 テーブルがある場合、 **column_set**、スパース列は個別の列として処理されません。 値にすべてのスパース列の値が含まれている、 **column_set**、XML 列と同じ方法でエクスポートするは、として**varbinary (max)** 場合としてまたはバイナリ型としてバインドされている**nvarchar (max)** 場合としてバインドされている、 **char**または**wchar**型)。 インポート時に、 **column_set**値は、のスキーマに準拠している必要があります、 **column_set**です。  
  
 **Queryout**操作を明示的に参照されている列の処理方法に変更はありません。 **column_set**列が XML 列と同じ動作があるし、スパースかどうかも何も起こりませんの取り扱いをスパース列をという名前です。  
  
 ただし場合、 **queryout**使用は、スパース列セットを名前のメンバーであるスパース列を参照するは、エクスポートしてには、同じ構造のテーブルに直接インポートを行うことはできません。 これは、BCP と一貫したメタデータを使用するため、**選択\***  、インポート操作に一致するようになって、 **column_set**このメタデータを持つメンバーの列です。 インポートする**column_set**メンバーの列の個別に、目的が参照するテーブルのビューを定義する必要があります**column_set**列、およびするが、ビューを使用してインポート操作を実行する必要があります。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server](../../oledb/oledb-driver-for-sql-server.md)  
  
  
