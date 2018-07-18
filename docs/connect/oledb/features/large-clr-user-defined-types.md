---
title: 大きな CLR ユーザー定義型 |Microsoft ドキュメント
description: 大きな CLR ユーザー定義型の OLE DB Driver for SQL Server
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
- large CLR user-defined types
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: efb6e8f00859e98963dbf4f511899ef517c5f7c0
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2018
ms.locfileid: "35611707"
---
# <a name="large-clr-user-defined-types"></a>大きな CLR ユーザー定義型
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server 2005 では、共通言語ランタイム (CLR) のユーザー定義型 (UDT) のサイズは 8,000 バイトに制限されていました。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降では、この制限が解除されます。 CLR UDT はラージ オブジェクト (LOB) 型と同様に扱われるようになりました。 つまり、8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作しますが、8,000 バイトを超える UDT もサポートされるようになり、そのサイズは "無制限" として報告されます。  
  
 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;OLE DB&#41;](../../oledb/ole-db/large-clr-user-defined-types-ole-db.md)です。  
  
## <a name="use-cases"></a>例   
  
 OLE DB では、大きな Udt のサポートには、ISequentialStream バインドを使用して、サーバーとの間の UDT 値のストリームに機能が含まれています。  
  
 8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作します。 OLE db の場合は、ISequentialStream バインドを使用してまだ小さな Udt をストリーミングできます。  
  
 場合によっては、ネイティブ コードで CLR UDT のコンテンツを認識する必要がありますが、マネージ オブジェクトのインスタンスを作成する必要はありません。 この場合は、カスタムのシリアル化を使用して、サーバーの UDT 値をクライアントで認識される形式に変換することができます。  
  
 既存のデータ アクセス コードを使用するアプリケーションの場合は、クライアント側で CLR UDT の動作を利用できます。そのためには、ネイティブ API を使用して UDT を取得し、混合モードのアプリケーションで C++ CLI 相互運用機能を使用して UDT のインスタンスを作成します。  
  
## <a name="see-also"></a>参照  
 [OLE DB Driver for SQL Server の機能](../../oledb/features/oledb-driver-for-sql-server-features.md)    
  
  
