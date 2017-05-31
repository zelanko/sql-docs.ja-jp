---
title: "クエリ ストアのワークロードを使用してデータベースをチューニングする | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Engine Tuning Advisor, Query Store
ms.assetid: 17107549-5073-4fa2-8ee7-5ed33b38821e
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 7f89ed5e87b8fd51e8618a8559679225d91b32de
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="tuning-database-using-workload-from-query-store"></a>クエリ ストアのワークロードを使用してデータベースをチューニングする
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]


SQL Server の[クエリ ストア](../../relational-databases/performance/how-query-store-collects-data.md)機能では、クエリ履歴、計画、および実行時統計を自動的にキャプチャし、これらの情報をデータベース内に保持します。 [データベース エンジン チューニング アドバイザー (DTA)](../../relational-databases/performance/database-engine-tuning-advisor.md) は、クエリ ストアを使用してチューニングの適切なワークロードを自動的に選択するという新しいオプションをサポートしています。 大半のユーザーは、この機能を使用すれば、チューニングのワークロードを明示的に収集する必要がなくなります。 この機能は、データベースでクエリ ストア機能がオンになっている場合のみ有効です。 
  
  この機能は、バージョン **16.4** 以降の SQL Server Management Studio で使用できます。 
  
<a name="how-to-tune-a-workload-from-query-store-in-database-engine-tuning-advisor-gui"></a>データベース エンジン チューニング アドバイザー GUI でクエリ ストアからのワークロードをチューニングする方法
---
DTA の GUI で、**[全般]** ペインの **[クエリ ストア]** をクリックして、この機能を有効にします (以下の図を参照)。
![クエリ ストアからの DTA ワークロード](../../relational-databases/performance/media/dta-workload-from-query-store.gif)
 
<a name="how-to-tune-a-workload-from-query-store-in-dtaexe-command-line-utility"></a>dta.exe コマンド ライン ユーティリティでクエリ ストアからのワークロードをチューニングする方法
---
コマンド ライン (dta.exe) で **-iq** オプションを選択して、クエリ ストアからワークロードを選択します。 

コマンドラインでは 2 つの追加オプションがあり、クエリ ストアからのワークロード選択時に DTA の動作をチューニングするのに役立ちます。 これらのオプションは、GUI では使用できません。
  1. チューニングするワークロードのイベントの数: このオプションは **-n** コマンドライン引数を使用して指定され、チューニングするクエリ ストアからのイベントの数を制御することができます。 DTA でのこのオプションの既定値は 1000 です。 DTA は常に、総実行時間に対して最もコストの高いイベントを選択します。 
  
  2. チューニングするイベントの時刻ウィンドウ: クエリ ストアにはかなり前に実行されたクエリが含まれている場合があるので、このオプションを使用して、DTA でのチューニングのためにクエリが実行されたはずの過去の期間 (時間) を指定することができます。 このオプションは **-I** コマンドライン引数を使用して指定します。 

詳細については、「[dta Utilty](../../tools/dta/dta-utility.md)」 (dta ユーティリティ) を参照してください。

<a name="difference-between-using-workload-from-query-store-and-plan-cache"></a>クエリ ストアからのワークロードの使用とプラン キャッシュからのワークロードの使用の違い 
--- 
クエリ ストアとプラン キャッシュの違いは、前者には、データベースに対して実行されたクエリがより長い期間にわたって含まれているということです。クエリはサーバー再起動後も保持されています。 一方、プラン キャッシュ には、プランがメモリにキャッシュされている最近実行されたクエリのサブセットのみが含まれます。 サーバーが再起動すると、プラン キャッシュ内のエントリは破棄されます。

<a name="see-also"></a>参照 
--- 
[データベース エンジン チューニング アドバイザー](../../relational-databases/performance/database-engine-tuning-advisor.md)     
[チュートリアル: データベース エンジン チューニング アドバイザー](Tutorial:%20Database%20Engine%20Tuning%20Advisor.md)     
[クエリ ストアがデータを収集するしくみ](../../relational-databases/performance/how-query-store-collects-data.md)     
[クエリ ストアを使用する際の推奨事項](../../relational-databases/performance/best-practice-with-the-query-store.md)
