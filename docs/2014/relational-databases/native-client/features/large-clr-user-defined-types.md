---
title: 大きな CLR ユーザー定義型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a85d6672a7346b3962dca8d3826306defaa76099
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075965"
---
# <a name="large-clr-user-defined-types"></a>大きな CLR ユーザー定義型
  SQL Server 2005 では、共通言語ランタイム (CLR) のユーザー定義型 (UDT) のサイズは 8,000 バイトに制限されていました。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降では、この制限が解除されます。 CLR UDT はラージ オブジェクト (LOB) 型と同様に扱われるようになりました。 つまり、8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作しますが、8,000 バイトを超える UDT もサポートされるようになり、そのサイズは "無制限" として報告されます。  
  
 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;OLE DB&#41; ](../ole-db/large-clr-user-defined-types-ole-db.md)と[Large CLR User-Defined 型&#40;ODBC&#41;](../odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="use-cases"></a>例  
 ODBC の場合、大きな UDT のサポートには、UDT 値を実行時データ パラメーターとして個別に送信する機能が含まれています。 これは、SQLPutData を使用して行います。  
  
 OLE DB では、大きな Udt のサポートには、ISequentialStream バインドを使用して、サーバーとの間の UDT 値のストリームに機能が含まれています。  
  
 8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作します。 OLE db の場合は、ISequentialStream バインドを使用してまだ小さな Udt をストリーミングできます。  
  
 場合によっては、ネイティブ コードで CLR UDT のコンテンツを認識する必要がありますが、マネージ オブジェクトのインスタンスを作成する必要はありません。 この場合は、カスタムのシリアル化を使用して、サーバーの UDT 値をクライアントで認識される形式に変換することができます。  
  
 既存のデータ アクセス コードを使用するアプリケーションの場合は、クライアント側で CLR UDT の動作を利用できます。そのためには、ネイティブ API を使用して UDT を取得し、混合モードのアプリケーションで C++ CLI 相互運用機能を使用して UDT のインスタンスを作成します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  