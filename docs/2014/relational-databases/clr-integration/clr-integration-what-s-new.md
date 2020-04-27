---
title: CLR 統合の新&#39;Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 45e4f0578d06eeafc545bea2b6374a37b8ef7cbc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62874067"
---
# <a name="what39s-new-in-clr-integration"></a>CLR 統合の新機能&#39;
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の CLR 統合で新しくなった点は次のとおりです。  
  
-   CLR のバージョン 4 では、破損状態の例外を CLR データベース オブジェクトはキャッチしません。 これらの例外は、CLR 統合ホスト層でキャッチされるようになりました。 これらの例外は、コード属性 ([\<legacyCorruptedStateExceptionsPolicy> 要素](https://go.microsoft.com/fwlink/?LinkId=204954)) を設定することによって、CLR データベースコンポーネントによってキャッチされることがあります。 ただし、破損状態の例外が発生した場合の結果には信頼性がないため、この設定はお勧めできません。  
  
-   [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] には厳しいセキュリティ要件があるため、CLR データベース コンポーネントには、今後も CLR バージョン 2.0 で定義されたコード アクセス セキュリティ モデルが使用されます。  
  
-   CLR バージョン 4 では、`System.TimeSpan` 値の形式に誤りがあると、`System.FormatExceptions` が生成されます。 バージョン 4 未満の CLR では、`System.TimeSpan` 値の形式に誤りがあっても無視されていました。 CLR バージョン 4 未満の動作に依存するデータベース アプリケーションは、データベース互換性レベル (`ALTER DATABASE Compatibility Level`) を 100 以下にして実行する必要があります。 詳細については、「 [<TimeSpan_LegacyFormatMode> 要素](https://go.microsoft.com/fwlink/?LinkId=205109)」を参照してください。  
  
-   CLR のバージョン 4 は、Unicode 5.1 をサポートします。 アクセントや記号を含んだ並べ替えの処理が改善されます。 従来の並べ替え動作に依存したアプリケーションでは、互換性の問題が生じる場合があります。 従来の並べ替え動作を有効にするには、データベース互換性レベル (`ALTER DATABASE Compatibility Level`) を 100 以下に設定する必要があります。 この点をサポートするために、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では、.NET Framework 4 ディレクトリ (C:\Windows\Microsoft.NET\Framework\v4.0.30319) に sort00001000.dll がインストールされます。 詳細については、「 [ \<CompatSortNLSVersion> 要素](https://go.microsoft.com/fwlink/?LinkId=205110)」を参照してください。  
  
-   次の列が、 [sys. dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql)に追加さ`total_processor_time_ms`れ`total_allocated_memory_kb`ました`survived_memory_kb`:、、および。  
  
  
