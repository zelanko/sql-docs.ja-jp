---
title: マージ アーティクルの処理順序の指定 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], processing order
- merge replication [SQL Server replication], article processing order
ms.assetid: d151e2c5-cf50-4cb3-a829-8f32455dbd66
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cb5506a4279ecd11c31d860f68d4c3736425298b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52788534"
---
# <a name="specify-the-processing-order-of-merge-articles"></a>マージ アーティクルの処理順序の指定
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]以降では、マージ パブリケーションのアーティクルの既定の処理順序をオーバーライドすることができます。 これは、たとえば、トリガーを使用して参照整合性を定義し、これらのトリガーを特定の順序で起動する必要がある場合に便利です。  
  
 **アーティクルの処理順序を指定するには**  
  
-   レプリケーション TRANSACT-SQL プログラミング:[マージ テーブル アーティクルの処理順序の指定 (レプリケーション Transact-SQL プログラミング)](../publish/specify-the-processing-order-of-merge-table-articles.md)  
  
## <a name="how-processing-order-is-determined"></a>処理順序を決定する方法  
 マージ同期の際、既定ではアーティクルがオブジェクト間の依存関係で必要な順序で処理されます。依存関係には、ベース テーブルに対して定義されている宣言参照整合性 (DRI) 制約も含まれます。 同期処理では、テーブルに対する変更が列挙された後で、これらの変更が適用されます。 DRI が定義されておらず、テーブル アーティクル間に結合フィルターか論理レコードが存在する場合、フィルターや論理レコードで必要な順序でアーティクルが処理されます。 DRI、結合フィルター、論理レコード、またはその他の依存関係で他のアーティクルと関係付けられていないアーティクルは、システム テーブル [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) 内のアーティクル ニックネームに従って処理されます。  
  
 パブリケーションに **SalesOrderHeader** テーブルと **SalesOrderDetail** テーブルが含まれており、 **SalesOrderHeader** テーブルには主キー列 **SalesOrderID** があり、 **SalesOrderDetail** テーブルには対応する外部キー列 **SalesOrderID** があるとします。 同期の際、マージ レプリケーションでは、新しい行を **SalesOrderHeader** に挿入してから関連する行を **SalesOrderDetail**に挿入することで、外部キーの違反を防ぎます。 同様に、 **SalesOrderDetail** から行を削除した後で、関連する行を **SalesOrderHeader**から削除します。  
  
 ただし、アプリケーションによっては、DRI ではなくデータベース トリガーやアプリケーション レベルで参照整合性が設定されます。 上記のようなパブリケーションでは、DRI ではなく **SalesOrderDetail** テーブルの挿入トリガーによって、挿入を許可する前に、 **SalesOrderHeader** テーブルに関連する行があることを確認できる場合があります。 **SalesOrderHeader** の削除トリガーでは、削除を許可する前に、 **SalesOrderDetail** に関連する行がないことを確認できる場合があります。 マージ レプリケーションでは、アーティクルの処理順序を決定する際にトリガーは考慮されません。トリガーが起動されないとその結果がどのようになるかがわからないためです。 同様に、アプリケーション レベルで定義された制約も考慮されません。  
  
 トリガーやアプリケーション レベルで参照整合性を保つ場合は、アーティクルの処理順序を指定する必要があります。 トリガーの例では、アーティクルの順序が挿入の順序で決まるため、 **SalesOrderHeader** テーブルを **SalesOrderDetail**の前に処理するように指定します。 マージ レプリケーションでは、削除の場合、自動的に順序が逆になります。 アーティクルの順序がなくてもマージ レプリケーションは失敗しません。これは、制約違反が発生してもマージ エージェントで処理が継続され、他のアーティクルの処理を終えた後で操作が再試行されるためです。 アーティクルの順序を指定すると、再試行とそれに付随する追加の処理が不要になります。 誤った順序 (詳細レコードがヘッダー レコードの前に処理されるような順序など) を指定すると、マージ レプリケーションは成功するまで処理を再試行します。  
  
## <a name="see-also"></a>参照  
 [マージ レプリケーションのアーティクル オプション](article-options-for-merge-replication.md)   
 [論理レコードによる関連行への変更のグループ化](group-changes-to-related-rows-with-logical-records.md)   
 [Join Filters](join-filters.md)  
  
  
