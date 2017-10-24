---
title: "XML のセキュリティに関する考慮事項 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML security in ADO
ms.assetid: fadbd38e-6e7b-4b81-96ea-85169c664374
caps.latest.revision: 3
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fc94f80cde09f6ad55de3a108b6fd16ef74444f1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="xml-security-considerations"></a>XML のセキュリティに関する考慮事項
ADO を保存し、レコード セット オブジェクトの Open メソッドは、Internet Explorer で実行するセーフである操作は考慮されません。 したがって、アプリケーションまたはブラウザーでホストされるコントロールで実行されているスクリプト コードでこれらのメソッドを使用している場合、ブラウザーのセキュリティ構成すると、その動作に影響があります。  
  
 Internet Explorer 5 は、既定のインターネット ゾーンでこのような操作に対するセキュリティ制限を提供します。 その構成では、レコード セットはクライアントのローカル ファイル システムへのアクセスを行うまたはページのダウンロード元サーバーのドメイン外の任意のデータ ソースにアクセスできません。 具体的には、ブラウザー ホスト内の実行中、レコード セットに保存できますバックアップ ファイル、ページのダウンロード元となる、同じサーバー上にある場合にのみです。 同様に、ページがダウンロードされた、同じサーバーにファイルがある場合にのみファイルから読み込むことにより、レコード セットを開くことができます。  
  
## <a name="see-also"></a>参照  
 [XML 形式で保持するレコード](../../../ado/guide/data/persisting-records-in-xml-format.md)

