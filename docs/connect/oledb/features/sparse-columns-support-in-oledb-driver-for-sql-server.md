---
title: OLE DB Driver for SQL Server のスパース列のサポート | Microsoft Docs
description: OLE DB Driver for SQL Server のスパース列のサポート
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
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 1b2e03ba16922f4130203dd897612a418e456f5f
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43029761"
---
# <a name="sparse-columns-support-in-ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server のスパース列のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server には、スパース列がサポートしています。 スパース列の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]を参照してください[スパース列の使用](../../../relational-databases/tables/use-sparse-columns.md)と[列セットの使用](../../../relational-databases/tables/use-column-sets.md)します。  
  
 OLE DB driver for SQL Server のスパース列のサポートの詳細については[スパース列をサポート&#40;OLE DB&#41;](../../oledb/ole-db/sparse-columns-support-ole-db.md)します。  
  
 この機能を説明するサンプル アプリケーションについては、「[SQL Server データ プログラミング サンプル](http://msftdpprodsamples.codeplex.com/)」を参照してください。  
  
## <a name="user-scenarios-for-sparse-columns-and-ole-db-driver-for-sql-server"></a>スパース列と OLE DB Driver for SQL Server ユーザー シナリオ  
 次の表は、OLE DB driver のスパース列を含む SQL Server ユーザー、一般的なユーザー シナリオを示します。  
  
|シナリオ|動作|  
|--------------|--------------|  
|**選択\*テーブルから**または iopenrowset::openrowset します。|スパース **column_set** のメンバーでないすべての列と、スパース **column_set** のメンバーであるすべての NULL 以外の列の値を含む XML 列が返されます。|  
|名前で列を参照する。|スパース列かどうか、**column_set** のメンバーであるかどうかに関係なく、列を参照できます。|  
|XML 計算列を通じて **column_set** メンバー列にアクセスする。|スパース **column_set** のメンバーである列に、名前で **column_set** を選択してアクセスし、**column_set** 列の XML を更新して値を挿入および更新できます。<br /><br /> 値は、**column_set** 列のスキーマに準拠している必要があります。|  
|DBSCHEMA_COLUMNS スキーマ行セットをテーブル列を制限しない (OLE DB) のすべての列のメタデータを取得します。|**column_set** のメンバーでないすべての列について 1 つの行が返されます。 テーブルにスパース **column_set** がある場合は、そのスパースについて 1 つの行が返されます。<br /><br /> この場合、**column_set** のメンバーである列のメタデータは返されないことに注意してください。|  
|スパース列かどうか、**column_set** のメンバーかどうかに関係なく、すべての列のメタデータを取得する。 この場合、大量の行が返される可能性があります。|DBSCHEMA_COLUMNS_EXTENDED スキーマ行セットの idbschemarowset::getrowset を呼び出します。|  
|**column_set** のメンバーである列についてのみメタデータを取得する。 この場合、大量の行が返される可能性があります。|DBSCHEMA_SPARSE_COLUMN_SET スキーマ行セットの idbschemarowset::getrowset を呼び出します。|  
|列がスパース列かどうかを確認する。|DBSCHEMA_COLUMNS スキーマ行セットの SS_IS_SPARSE 列を調べます (OLE DB)。|  
|列が判断を**column_set**します。|DBSCHEMA_COLUMNS スキーマ行セットの SS_IS_COLUMN_SET 列を調べます。 または、 *dwFlags* icolumnsinfo::getcolumninfo または DBCOLUMNFLAGS icolumnsrowset::getcolumnsrowset によって返される行セットで返されます。 **column_set** 列の場合は DBCOLUMNFLAGS_SS_ISCOLUMNSET が設定されます。|  
|**column_set** を含まないテーブルに対して BCP でスパース列をインポートおよびエクスポートする。|ない動作の変更から以前のバージョンの OLE DB Driver for SQL Server。|  
|**column_set** を含むテーブルに対して BCP でスパース列をインポートおよびエクスポートする。|**Column_set**がインポートされ、XML と同じ方法でエクスポートは、として**varbinary (max)** 場合またはとしてバイナリの型としてバインドされている**nvarchar (max)** 場合として、バインド**char**または**wchar**型。<br /><br /> スパース **column_set** のメンバーである列は個別の列としてはエクスポートされず、**column_set** の値でのみエクスポートされます。|  
|**queryout** BCP の動作。|SQL Server の以前のバージョンの OLE DB ドライバーから明示的に名前付きの列の処理に変更はありません。<br /><br /> スキーマが異なる列の間のインポートおよびエクスポートを含むシナリオでは、特別な処理が必要になる場合があります。<br /><br /> BCP の詳細については、後の「一括コピー (BCP) によるスパース列のサポート」を参照してください。|  
  
## <a name="down-level-client-behavior"></a>下位クライアントの動作  
 下位クライアントでは、SQLColumns および DBSCHMA_COLUMNS でメタデータが返されるのは、スパース **column_set** のメンバーでない列のみです。
  
 下位クライアントでは、スパース **column_set** のメンバーである列に名前でアクセスできます。[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] クライアントでは、XML 列として **column_set** 列にアクセスできます。  
  
## <a name="bulk-copy-bcp-support-for-sparse-columns"></a>一括コピー (BCP) によるスパース列のサポート  
 OLE DB の BCP API には、スパース列や **column_set** 機能のための変更はありません。  
  
 テーブルに **column_set** がある場合、スパース列は個別の列として処理されません。 値のすべてのスパース列の値が含まれている、 **column_set**、これは、XML 列と同じ方法でエクスポートは、として**varbinary (max)** 場合またはとしてバイナリの型としてバインド**nvarchar (max)** 場合としてバインド、 **char**または**wchar**型)。 インポート時に、 **column_set**値は、のスキーマに準拠する必要があります、 **column_set**します。  
  
 **queryout** の操作については、明示的に参照されている列の処理方法は変更されていません。 **column_set** 列の動作は XML 列と同じで、名前で参照されているスパース列の処理には、列がスパース列であることの影響はありません。  
  
 ただし、**queryout** をエクスポートに使用する場合に、スパース列セットのメンバーであるスパース列を名前で参照すると、同じ構造のテーブルへの直接インポートができなくなります。 これは、BCP では **select \*** 操作と一貫したメタデータがインポートのために使用され、そのメタデータを **column_set** メンバー列と対応させることはできないからです。 **column_set** メンバー列を個別にインポートするには、目的の **column_set** 列を参照するテーブルのビューを定義して、そのビューを使用してインポート操作を行う必要があります。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server](../../oledb/oledb-driver-for-sql-server.md)  
  
  
