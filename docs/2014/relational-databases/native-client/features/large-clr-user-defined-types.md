---
title: 大きな CLR ユーザー定義型 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types
ms.assetid: b65eb61d-ccf6-49c0-98e7-9a4ef4b2f790
author: rothja
ms.author: jroth
ms.openlocfilehash: 27f0c13caea8c4aca63d78238509c6d05f1bf7bf
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85047920"
---
# <a name="large-clr-user-defined-types"></a>大きな CLR ユーザー定義型
  SQL Server 2005 では、共通言語ランタイム (CLR) のユーザー定義型 (UDT) のサイズは 8,000 バイトに制限されていました。 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降では、この制限が解除されます。 CLR UDT はラージ オブジェクト (LOB) 型と同様に扱われるようになりました。 つまり、8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作しますが、8,000 バイトを超える UDT もサポートされるようになり、そのサイズは "無制限" として報告されます。  
  
 詳細については、「 [&#40;&#41;OLE DB の大きな Clr ユーザー定義型](../ole-db/large-clr-user-defined-types-ole-db.md)」を参照してください。また、 [&#40;ODBC&#41;の大きな Clr ユーザー定義型](../odbc/large-clr-user-defined-types-odbc.md)については、「」を参照してください。  
  
## <a name="use-cases"></a>ユース ケース  
 ODBC の場合、大きな UDT のサポートには、UDT 値を実行時データ パラメーターとして個別に送信する機能が含まれています。 これを行うには、SQLPutData を使用します。  
  
 OLE DB の場合、大きな UDT のサポートには、ISequentialStream バインドを使用したサーバーとの間の UDT 値のストリームの送受信機能が含まれています。  
  
 8,000 バイト以下の UDT は SQL Server 2005 の場合と同じように動作します。 OLE DB では、ISequentialStream バインドを使用して、小さな UDT をストリーム処理することもできます。  
  
 場合によっては、ネイティブ コードで CLR UDT のコンテンツを認識する必要がありますが、マネージド オブジェクトのインスタンスを作成する必要はありません。 この場合は、カスタムのシリアル化を使用して、サーバーの UDT 値をクライアントで認識される形式に変換することができます。  
  
 既存のデータ アクセス コードを使用するアプリケーションの場合は、クライアント側で CLR UDT の動作を利用できます。そのためには、ネイティブ API を使用して UDT を取得し、混合モードのアプリケーションで C++ CLI 相互運用機能を使用して UDT のインスタンスを作成します。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  
