---
title: IOpenRowset を使用した行セットの作成 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IOpenRowset interface
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
ms.assetid: e8bc3de7-4b97-4de9-8df8-e11947d24045
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: b4a38eba623e91b063985fbc6924b87648cb8d58
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37432621"
---
# <a name="creating-a-rowset-with-iopenrowset"></a>IOpenRowset を使用した行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのサポート、 **iopenrowset::openrowset**メソッドは、次の制限。  
  
-   ベース テーブルまたはビューを指定してください、データベースの ID (DBID) 構造体、 *pTableID*パラメーターを指します。  
  
-   DBID *eKind*メンバーは DBKIND_NAME を指定する必要があります。  
  
-   DBID *uName*メンバーは、Unicode 文字の文字列として既存のベース テーブルまたはビューの名前を指定する必要があります。  
  
-   *PIndexID*パラメーターの**OpenRowset** NULL にする必要があります。  
  
 結果セットは**iopenrowset::openrowset** 1 つの行セットが含まれています。 1 つの行セットを含む結果セットをサポートできる[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]カーソル。 開発者はカーソル サポートによって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の同時実行メカニズムを使用できます。  
  
## <a name="see-also"></a>参照  
 [行セット](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
