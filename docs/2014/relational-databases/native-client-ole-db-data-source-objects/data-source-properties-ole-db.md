---
title: データ ソースのプロパティ (OLE DB) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, data source properties
- properties [OLE DB]
- data source properties [OLE DB]
- OLE DB data source properties [SQL Server Native Client]
ms.assetid: 6e14fefc-4e0b-4847-a833-4cf0abe65d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 094bcbe48fa6c4cf09120b1dcf835c08199f10d1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48074132"
---
# <a name="data-source-properties-ole-db"></a>データ ソースのプロパティ (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがデータ ソースのプロパティを次のように実装します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|DBPROP_CURRENTCATALOG|R/W: 読み取り/書き込み&lt;br&gt;&lt;/br&gt;既定値 : なし<br /><br /> 説明: DBPROP_CURRENTCATALOG の値をレポートの現在のデータベース、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー セッション。 このプロパティ値を設定することは、[!INCLUDE[tsql](../../includes/tsql-md.md)] USE *database* ステートメントを使用して現在のデータベースを設定するのと同じ効果があります。<br /><br /> [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンでは、データベース名を小文字で指定して [sp_defaultdb](/sql/relational-databases/system-stored-procedures/sp-defaultdb-transact-sql) を呼び出すと、大文字と小文字が混在する名前を使用してデータベースが作成されている場合でも、DBPROP_CURRENTCATALOG では名前が小文字で返されます。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、大文字と小文字が混在する名前が DBPROP_CURRENTCATALOG によって返されます。|  
|DBPROP_MULTIPLECONNECTIONS|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : 行セットを生成しないコマンドまたはサーバー カーソルではない行セットを生成するコマンドが接続で実行されているときに、ユーザーが別のコマンドを実行すると、DBPROP_MULTIPLECONNECTIONS が VARIANT_TRUE に設定されている場合は、新しいコマンドを実行するために新しい接続が作成されます。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DBPROP_MULTIPLECONNECTION が VARIANT_FALSE の場合、またはトランザクションの接続でアクティブな場合は、Native Client OLE DB プロバイダーに別の接続は作成されません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー DBPROP_MULTIPLECONNECTIONS が VARIANT_FALSE に、アクティブなトランザクションがある場合は E_FAIL を返します DB_E_OBJECTOPEN が返されます。 トランザクションとロックは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって接続ごとに管理されます。 2 番目の接続を作成する場合は、個別の接続のコマンドではロックは共有されません。 あるコマンドで別のコマンドがブロックされないようにするには、他のコマンドによって要求される行にロックを設定します。 このことは、複数のセッションを作成する場合にも適用されます。<br /><br /> 各セッションには個別の接続があります。|  
  
 プロバイダー固有のプロパティ セット DBPROPSET_SQLSERVERDATASOURCE、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、次の追加のデータ ソースのプロパティを定義します。  
  
|プロパティ ID|説明|  
|-----------------|-----------------|  
|SSPROP_ENABLEFASTLOAD|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : メモリからの一括コピーを有効にするには、SSPROP_ENABLEFASTLOAD プロパティを VARIANT_TRUE に設定する必要があります。 このプロパティをデータ ソースで設定すると、新しく作成されたセッションを使用して、コンシューマーから [IRowsetFastLoad](../native-client-ole-db-interfaces/irowsetfastload-ole-db.md) インターフェイスにアクセスできます。<br /><br /> このプロパティを VARIANT_TRUE に設定している場合、**IID_IRowsetFastLoad** インターフェイスを要求するか、**SSPROP_IRowsetFastLoad** を VARIANT_TRUE に設定すると、**IOpenRowset::OpenRowset** を介して **IRowsetFastLoad** インターフェイスが使用可能になります。|  
|SSPROP_ENABLEBULKCOPY|R/W : 読み取り/書き込み<br></br>既定値 : VARIANT_FALSE<br /><br /> 説明 : ファイルからの一括コピーを有効にするには、SSPROP_ENABLEBULKCOPY プロパティを VARIANT_TRUE に設定する必要があります。 データ ソースにこのプロパティを設定すると、コンシューマーから IBCPSession インターフェイスにセッションと同じレベルでアクセスできるようになります。<br /><br /> また、SSPROP_IRowsetFastLoad を VARIANT_TRUE に設定する必要があります。|  
  
## <a name="see-also"></a>参照  
 [データ ソース オブジェクト&#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
  
