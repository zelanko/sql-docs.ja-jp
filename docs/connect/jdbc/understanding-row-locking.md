---
title: 行ロックについて |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25c0e5c3b6026f56f6390faba960d64323e0f5d2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-row-locking"></a>行ロックについて
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]行ロック。 これらには、データベースへの変更を複数のユーザーが同時に行う際の同時実行制御が実装されています。 既定では、トランザクションとロックは接続ごとに管理されます。 たとえば、アプリケーションで 2 つの JDBC 接続が開かれている場合、一方の接続で取得したロックをもう一方の接続と共有することはできません。 どちらの接続でも、もう一方の接続によって保持されているロックと競合するロックは取得できません。  
  
> [!NOTE]  
>  行ロックの使用時にはフェッチ バッファー内のすべての行がロックされるため、フェッチ サイズを非常に大きく設定すると、同時実行性に影響を与える可能性があります。  
  
 ロックは、トランザクションの整合性とデータベースの一貫性を保つために使用します。 ロックを使用すると、他のユーザーがデータを変更している最中にそのデータを読み取ったり、複数のユーザーが同時に同一のデータを変更したりする危険性を回避できます。 ロックを使用しないと、データベース内のデータが論理的に正しくなくなったり、そのデータに対して実行したクエリから予期しない結果が返されたりする可能性があります。  
  
> [!NOTE]  
>  行ロックの詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]を参照してください"内のロック、 [!INCLUDE[ssDE](../../includes/ssde_md.md)]"で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
