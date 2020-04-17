---
title: CLR 統合の新機能 |マイクロソフトドキュメント
description: CLR をホストする SQL サーバーは、CLR 統合と呼ばれます。 この資料では、SQL Server 2012 の CLR 統合の新機能について説明します。
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: d27bf0d925d3a98dda488fb85aff7446434cc8ad
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488091"
---
# <a name="clr-integration---what39s-new"></a>CLR 統合 - 新機能&#39;
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] の CLR 統合で新しくなった点は次のとおりです。  
  
-   CLR のバージョン 4 では、破損状態の例外を CLR データベース オブジェクトはキャッチしません。 これらの例外は、CLR 統合ホスト層でキャッチされるようになりました。 これらの例外は、コード属性 ([\<legacyの破損状態の例外ポリシー>要素](https://go.microsoft.com/fwlink/?LinkId=204954)) を設定することで、CLR データベース コンポーネントによってキャッチできます。 ただし、破損状態の例外が発生した場合の結果には信頼性がないため、この設定はお勧めできません。  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] には厳しいセキュリティ要件があるため、CLR データベース コンポーネントには、今後も CLR バージョン 2.0 で定義されたコード アクセス セキュリティ モデルが使用されます。  
  
-   CLR バージョン 4 では **、System.TimeSpan**値の形式エラーが発生**します。** CLR のバージョン 4 より前のバージョンでは **、System.TimeSpan**値の形式エラーは無視されていました。 CLR のバージョン 4 より前の動作に依存するデータベース アプリケーションは、データベース互換性レベル (**ALTER DATABASE 互換性レベル**) 100 以下で実行する必要があります。 詳細については、「 [>要素<TimeSpan_LegacyFormatMode」](https://go.microsoft.com/fwlink/?LinkId=205109)を参照してください。  
  
-   CLR のバージョン 4 は、Unicode 5.1 をサポートします。 アクセントや記号を含んだ並べ替えの処理が改善されます。 従来の並べ替え動作に依存したアプリケーションでは、互換性の問題が生じる場合があります。 従来の並べ替えを有効にするには、データベース互換性レベル (**ALTER DATABASE 互換性レベル**) を 100 以下に設定する必要があります。 この点をサポートするために、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、.NET Framework 4 ディレクトリ (C:\Windows\Microsoft.NET\Framework\v4.0.30319) に sort00001000.dll がインストールされます。 詳細については、「要素の[\<互換ソートNLSVersion>」](https://go.microsoft.com/fwlink/?LinkId=205110)を参照してください。  
  
-   次の列が[sys.dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md)に追加されました: **total_processor_time_ms**、 **total_allocated_memory_kb**、および**survived_memory_kb**。  
  
  
