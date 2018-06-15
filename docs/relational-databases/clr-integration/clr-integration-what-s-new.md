---
title: どのような&#39;CLR 統合の |Microsoft ドキュメント
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: clr
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
caps.latest.revision: 7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 040f31cc5cfd3cc06cb20e298a275188fc616185
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32920067"
---
# <a name="clr-integration---what39s-new"></a>CLR 統合の新機能&#39;s New
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] の CLR 統合で新しくなった点は次のとおりです。  
  
-   CLR のバージョン 4 では、破損状態の例外を CLR データベース オブジェクトはキャッチしません。 これらの例外は、CLR 統合ホスト層でキャッチされるようになりました。 これらの例外を引き続きキャッチできますが、CLR データベース コンポーネント コード属性を設定して ([\<legacyCorruptedStateExceptionsPolicy > 要素](http://go.microsoft.com/fwlink/?LinkId=204954))。 ただし、破損状態の例外が発生した場合の結果には信頼性がないため、この設定はお勧めできません。  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] には厳しいセキュリティ要件があるため、CLR データベース コンポーネントには、今後も CLR バージョン 2.0 で定義されたコード アクセス セキュリティ モデルが使用されます。  
  
-   CLR バージョン 4 に形式エラーで、 **System.TimeSpan**値が生成されます、 **System.FormatExceptions**です。 形式エラー、CLR の version 4 より前、 **System.TimeSpan**値は無視されました。 データベースの互換性レベルに、CLR の version 4 より前の動作に依存するデータベース アプリケーションを実行する必要があります (**ALTER DATABASE 互換性レベル**) を 100 以下です。 詳細については、次を参照してください。 [< TimeSpan_LegacyFormatMode > 要素](http://go.microsoft.com/fwlink/?LinkId=205109)です。  
  
-   CLR のバージョン 4 は、Unicode 5.1 をサポートします。 アクセントや記号を含んだ並べ替えの処理が改善されます。 従来の並べ替え動作に依存したアプリケーションでは、互換性の問題が生じる場合があります。 従来の並べ替え、データベースの互換性レベルを有効にする (**ALTER DATABASE 互換性レベル**) を 100 以下に設定する必要があります。 この点をサポートするために、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、.NET Framework 4 ディレクトリ (C:\Windows\Microsoft.NET\Framework\v4.0.30319) に sort00001000.dll がインストールされます。 詳細については、次を参照してください。 [ \<CompatSortNLSVersion > 要素](http://go.microsoft.com/fwlink/?LinkId=205110)です。  
  
-   次の列が追加されて[sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md): **total_processor_time_ms**、 **total_allocated_memory_kb**、および**survived_memory_kb**です。  
  
  
