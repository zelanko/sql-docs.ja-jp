---
title: "データ ソースのプロパティ (OLE DB) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-data-source-objects
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 6e14fefc-4e0b-4847-a833-4cf0abe65d50
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 31983f3c9884f12aa33e6ff8ab7397e8f0c3c5c5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="data-source-properties-ole-db"></a>データ ソースのプロパティ (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがデータ ソースのプロパティを次のように実装します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R/W: 読み取り/書き込み&lt;br&gt;&lt;/br&gt;既定値 : なし<br /><br /> 説明: DBPROP_CURRENTCATALOG の値をレポートの現在のデータベース、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー セッションです。 使用して、現在のデータベースを設定するのと同じ効果を持つプロパティ値を設定、[!INCLUDE[tsql](../../includes/tsql-md.md)]使用*データベース*ステートメントです。<br /><br /> 以降で[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]を呼び出す場合は、 [sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md)データベース名を指定し、小文字で、データベースは、混在のケースの名前を持つ最初に作成された場合でも DBPROP_CURRENTCATALOG は名前を返しますで小文字に変換します。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、大文字と小文字が混在する名前が DBPROP_CURRENTCATALOG によって返されます。|  
|DBPROP_MULTIPLECONNECTIONS|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : 行セットを生成しないコマンドまたはサーバー カーソルではない行セットを生成するコマンドが接続で実行されているときに、ユーザーが別のコマンドを実行すると、DBPROP_MULTIPLECONNECTIONS が VARIANT_TRUE に設定されている場合は、新しいコマンドを実行するために新しい接続が作成されます。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBPROP_MULTIPLECONNECTION が VARIANT_FALSE の場合、またはトランザクションの接続でアクティブな場合は、Native Client OLE DB プロバイダーに別の接続は作成できません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBPROP_MULTIPLECONNECTIONS が VARIANT_FALSE に、E_FAIL が返された場合は、アクティブなトランザクションがある場合、Native Client OLE DB プロバイダーから DB_E_OBJECTOPEN が返されます。 トランザクションとロックは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって接続ごとに管理されます。 2 番目の接続を作成する場合は、個別の接続のコマンドではロックは共有されません。 あるコマンドで別のコマンドがブロックされないようにするには、他のコマンドによって要求される行にロックを設定します。 このことは、複数のセッションを作成する場合にも適用されます。<br /><br /> 各セッションには個別の接続があります。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERDATASOURCE、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次の追加のデータ ソースのプロパティを定義します。  
  
|プロパティ ID|Description|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : メモリからの一括コピーを有効にするには、SSPROP_ENABLEFASTLOAD プロパティを VARIANT_TRUE に設定する必要があります。 このプロパティをデータ ソースに設定すると、新しく作成されたセッションでは消費者のアクセスを[IRowsetFastLoad](../../relational-databases/native-client-ole-db-interfaces/irowsetfastload-ole-db.md)インターフェイスです。<br /><br /> プロパティが VARIANT_TRUE に設定されている場合**IRowsetFastLoad**インターフェイスを使用してを通じて**iopenrowset::openrowset**要求することによって、 **IID_IRowsetFastLoad**インターフェイスかを設定**SSPROP_IRowsetFastLoad**を VARIANT_TRUE に設定します。|  
|SSPROP_ENABLEBULKCOPY|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : ファイルからの一括コピーを有効にするには、SSPROP_ENABLEBULKCOPY プロパティを VARIANT_TRUE に設定する必要があります。 データ ソースにこのプロパティを設定すると、コンシューマーから IBCPSession インターフェイスにセッションと同じレベルでアクセスできるようになります。<br /><br /> また、SSPROP_IRowsetFastLoad を VARIANT_TRUE に設定する必要があります。|  
  
## <a name="see-also"></a>参照  
 [データ ソース オブジェクト &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
