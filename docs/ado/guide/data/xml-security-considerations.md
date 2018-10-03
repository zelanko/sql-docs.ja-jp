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
manager: craigg
ms.openlocfilehash: e80a0bbb70a626ff01043592896ecfbe3c21f189
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47802883"
---
# <a name="xml-security-considerations"></a>XML のセキュリティに関する考慮事項
ADO を保存し、レコード セット オブジェクトで Open メソッドは、Internet Explorer で実行する安全な操作は考慮されません。 そのため、アプリケーションまたはブラウザーでホストされているコントロールで実行されているスクリプト コードでこれらのメソッドを使用する場合、ブラウザーのセキュリティの構成は、動作に影響があります。  
  
 Internet Explorer 5 では、既定では、インターネット ゾーンでこのような操作に対するセキュリティ制限を提供します。 その構成では、レコード セットはクライアント上のローカル ファイル システムへのアクセスを行うまたはページのダウンロード元のサーバーのドメインの外部データ ソースにアクセスできません。 具体的には、ブラウザーのホスト内での実行中、レコード セットに保存できます戻るファイル ページがダウンロードされた、同じサーバー上にある場合にのみ。 同様に、ページがダウンロードされた、同じサーバーにファイルがある場合にのみファイルから読み込むことによって、レコード セットを開くことができます。  
  
## <a name="see-also"></a>参照  
 [レコードを XML 形式で保持する](../../../ado/guide/data/persisting-records-in-xml-format.md)
