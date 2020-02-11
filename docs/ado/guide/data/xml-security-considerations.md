---
title: XML のセキュリティに関する考慮事項 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fa0e9e2df1e8ba3f44b10e662d25e536ac7962f8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923353"
---
# <a name="xml-security-considerations"></a>XML のセキュリティに関する考慮事項
Recordset オブジェクトの ADO Save および Open メソッドは、Internet Explorer で実行するための安全な操作とは見なされません。 このため、これらのメソッドが、ブラウザーでホストされているアプリケーションまたはコントロールで実行されているスクリプトコードで使用されている場合、ブラウザーのセキュリティ構成はその動作に影響します。  
  
 Internet Explorer 5 では、インターネットゾーンの既定では、このような操作に対してセキュリティ上の制限があります。 その構成では、レコードセットによって、クライアント上のローカルファイルシステムへのアクセスを許可したり、ページのダウンロード元のサーバーのドメインの外部にあるデータソースにアクセスしたりすることはできません。 具体的には、ブラウザーホスト内で実行されている場合、レコードセットは、ページのダウンロード元と同じサーバー上にある場合にのみ、ファイルに保存できます。 同様に、ファイルからファイルを読み込んでレコードセットを開くこともできます。その場合は、そのファイルが、ページのダウンロード元と同じサーバー上にある場合に限られます。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
