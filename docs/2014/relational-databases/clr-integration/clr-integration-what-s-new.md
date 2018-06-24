---
title: どのような&#39;CLR 統合の |Microsoft ドキュメント
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
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
caps.latest.revision: 6
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5cc1f1674a4704ad156212744025ec1d98422a24
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074847"
---
# <a name="what39s-new-in-clr-integration"></a>どのような&#39;の CLR 統合
  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の CLR 統合で新しくなった点は次のとおりです。  
  
-   CLR のバージョン 4 では、破損状態の例外を CLR データベース オブジェクトはキャッチしません。 これらの例外は、CLR 統合ホスト層でキャッチされるようになりました。 これらの例外を引き続きキャッチできますが、CLR データベース コンポーネント コード属性を設定して ([\<legacyCorruptedStateExceptionsPolicy > 要素](http://go.microsoft.com/fwlink/?LinkId=204954))。 ただし、破損状態の例外が発生した場合の結果には信頼性がないため、この設定はお勧めできません。  
  
-   [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] には厳しいセキュリティ要件があるため、CLR データベース コンポーネントには、今後も CLR バージョン 2.0 で定義されたコード アクセス セキュリティ モデルが使用されます。  
  
-   CLR バージョン 4 では、`System.TimeSpan` 値の形式に誤りがあると、`System.FormatExceptions` が生成されます。 バージョン 4 未満の CLR では、`System.TimeSpan` 値の形式に誤りがあっても無視されていました。 CLR バージョン 4 未満の動作に依存するデータベース アプリケーションは、データベース互換性レベル (`ALTER DATABASE Compatibility Level`) を 100 以下にして実行する必要があります。 詳細については、次を参照してください。 [< TimeSpan_LegacyFormatMode > 要素](http://go.microsoft.com/fwlink/?LinkId=205109)です。  
  
-   CLR のバージョン 4 は、Unicode 5.1 をサポートします。 アクセントや記号を含んだ並べ替えの処理が改善されます。 従来の並べ替え動作に依存したアプリケーションでは、互換性の問題が生じる場合があります。 従来の並べ替え動作を有効にするには、データベース互換性レベル (`ALTER DATABASE Compatibility Level`) を 100 以下に設定する必要があります。 この点をサポートするために、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では、.NET Framework 4 ディレクトリ (C:\Windows\Microsoft.NET\Framework\v4.0.30319) に sort00001000.dll がインストールされます。 詳細については、次を参照してください。 [ \<CompatSortNLSVersion > 要素](http://go.microsoft.com/fwlink/?LinkId=205110)です。  
  
-   次の列が追加されて[sys.dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql): `total_processor_time_ms`、 `total_allocated_memory_kb`、および`survived_memory_kb`です。  
  
  
