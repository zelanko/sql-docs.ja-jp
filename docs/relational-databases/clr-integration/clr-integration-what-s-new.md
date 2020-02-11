---
title: CLR 統合の新&#39;Microsoft Docs
ms.date: 03/03/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: clr
ms.topic: conceptual
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d37d476808f80cf132037542d17cb3de61eeccc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68134874"
---
# <a name="clr-integration---what39s-new"></a>CLR 統合-&#39;の新機能
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] の CLR 統合で新しくなった点は次のとおりです。  
  
-   CLR のバージョン 4 では、破損状態の例外を CLR データベース オブジェクトはキャッチしません。 これらの例外は、CLR 統合ホスト層でキャッチされるようになりました。 これらの例外は、コード属性 ([\<legacyCorruptedStateExceptionsPolicy> 要素](https://go.microsoft.com/fwlink/?LinkId=204954)) を設定することによって、CLR データベースコンポーネントによってキャッチされることがあります。 ただし、破損状態の例外が発生した場合の結果には信頼性がないため、この設定はお勧めできません。  
  
-   
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] には厳しいセキュリティ要件があるため、CLR データベース コンポーネントには、今後も CLR バージョン 2.0 で定義されたコード アクセス セキュリティ モデルが使用されます。  
  
-   CLR バージョン4では、 **TimeSpan**値の形式エラーによって、system.string**例外**が生成されます。 CLR のバージョン4より前では、 **TimeSpan**値の形式エラーは無視されました。 CLR のバージョン4より前の動作に依存するデータベースアプリケーションは、データベース互換性レベル (**ALTER Database Compatibility level**) が100以下で実行する必要があります。 詳細については、「 [<TimeSpan_LegacyFormatMode> 要素](https://go.microsoft.com/fwlink/?LinkId=205109)」を参照してください。  
  
-   CLR のバージョン 4 は、Unicode 5.1 をサポートします。 アクセントや記号を含んだ並べ替えの処理が改善されます。 従来の並べ替え動作に依存したアプリケーションでは、互換性の問題が生じる場合があります。 従来の並べ替えを有効にするには、データベースの互換性レベル (**ALTER Database Compatibility level**) を100以下に設定する必要があります。 この点をサポートするために、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、.NET Framework 4 ディレクトリ (C:\Windows\Microsoft.NET\Framework\v4.0.30319) に sort00001000.dll がインストールされます。 詳細については、「 [ \<CompatSortNLSVersion> 要素](https://go.microsoft.com/fwlink/?LinkId=205110)」を参照してください。  
  
-   次の列が、 [sys. dm_clr_appdomains](../../relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql.md)に追加されました: **total_processor_time_ms**、 **total_allocated_memory_kb**、および**survived_memory_kb**。  
  
  
