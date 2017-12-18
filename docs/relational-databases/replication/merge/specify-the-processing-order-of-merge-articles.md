---
title: "マージ アーティクルの処理順序の指定 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: d151e2c5-cf50-4cb3-a829-8f32455dbd66
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1cb9d8b566766e23bfb17bc93b53d9d222fa3895
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="specify-the-processing-order-of-merge-articles"></a>マージ アーティクルの処理順序の指定
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降では、マージ パブリケーションのアーティクルの既定の処理順序を上書きすることができます。 これは、たとえば、トリガーを使用して参照整合性を定義し、これらのトリガーを特定の順序で起動する必要がある場合に便利です。  
  
 **アーティクルの処理順序を指定するには**  
  
-   レプリケーション Transact-SQL プログラミング: [マージ テーブル アーティクルの処理順序の指定 &#40;レプリケーション Transact-SQL プログラミング&#41;](../../../relational-databases/replication/publish/specify-the-processing-order-of-merge-table-articles.md)  
  
## <a name="how-processing-order-is-determined"></a>処理順序を決定する方法  
 マージ同期の際、既定ではアーティクルがオブジェクト間の依存関係で必要な順序で処理されます。依存関係には、ベース テーブルに対して定義されている宣言参照整合性 (DRI) 制約も含まれます。 同期処理では、テーブルに対する変更が列挙された後で、これらの変更が適用されます。 DRI が定義されておらず、テーブル アーティクル間に結合フィルターか論理レコードが存在する場合、フィルターや論理レコードで必要な順序でアーティクルが処理されます。 DRI、結合フィルター、論理レコード、またはその他の依存関係で他のアーティクルと関係付けられていないアーティクルは、システム テーブル [sysmergearticles &#40;Transact-SQL&#41;](../../../relational-databases/system-tables/sysmergearticles-transact-sql.md) 内のアーティクル ニックネームに従って処理されます。  
  
 パブリケーションに **SalesOrderHeader** テーブルと **SalesOrderDetail** テーブルが含まれており、 **SalesOrderHeader** テーブルには主キー列 **SalesOrderID** があり、 **SalesOrderDetail** テーブルには対応する外部キー列 **SalesOrderID** があるとします。 同期の際、マージ レプリケーションでは、新しい行を **SalesOrderHeader** に挿入してから関連する行を **SalesOrderDetail**に挿入することで、外部キーの違反を防ぎます。 同様に、 **SalesOrderDetail** から行を削除した後で、関連する行を **SalesOrderHeader**から削除します。  
  
 ただし、アプリケーションによっては、DRI ではなくデータベース トリガーやアプリケーション レベルで参照整合性が設定されます。 上記のようなパブリケーションでは、DRI ではなく **SalesOrderDetail** テーブルの挿入トリガーによって、挿入を許可する前に、 **SalesOrderHeader** テーブルに関連する行があることを確認できる場合があります。 **SalesOrderHeader** の削除トリガーでは、削除を許可する前に、 **SalesOrderDetail** に関連する行がないことを確認できる場合があります。 マージ レプリケーションでは、アーティクルの処理順序を決定する際にトリガーは考慮されません。トリガーが起動されないとその結果がどのようになるかがわからないためです。 同様に、アプリケーション レベルで定義された制約も考慮されません。  
  
 トリガーやアプリケーション レベルで参照整合性を保つ場合は、アーティクルの処理順序を指定する必要があります。 トリガーの例では、アーティクルの順序が挿入の順序で決まるため、 **SalesOrderHeader** テーブルを **SalesOrderDetail**の前に処理するように指定します。 マージ レプリケーションでは、削除の場合、自動的に順序が逆になります。 アーティクルの順序がなくてもマージ レプリケーションは失敗しません。これは、制約違反が発生してもマージ エージェントで処理が継続され、他のアーティクルの処理を終えた後で操作が再試行されるためです。 アーティクルの順序を指定すると、再試行とそれに付随する追加の処理が不要になります。 誤った順序 (詳細レコードがヘッダー レコードの前に処理されるような順序など) を指定すると、マージ レプリケーションは成功するまで処理を再試行します。  
  
## <a name="see-also"></a>参照  
 [マージ レプリケーションのアーティクル オプション](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [論理レコードによる関連行への変更のグループ化](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [Join Filters](../../../relational-databases/replication/merge/join-filters.md)  
  
  
