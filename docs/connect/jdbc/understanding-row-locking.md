---
title: 行ロックについて |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cdf5ca943ec4d823c8c568f0818a49c44f22cbe6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38040780"
---
# <a name="understanding-row-locking"></a>行ロックについて
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の行ロックを使用します。 これらには、データベースへの変更を複数のユーザーが同時に行う際の同時実行制御が実装されています。 既定では、トランザクションとロックは接続ごとに管理されます。 たとえば、アプリケーションで 2 つの JDBC 接続が開かれている場合、一方の接続で取得したロックをもう一方の接続と共有することはできません。 どちらの接続でも、もう一方の接続によって保持されているロックと競合するロックは取得できません。  
  
> [!NOTE]  
>  行ロックの使用時にはフェッチ バッファー内のすべての行がロックされるため、フェッチ サイズを非常に大きく設定すると、同時実行性に影響を与える可能性があります。  
  
 ロックは、トランザクションの整合性とデータベースの一貫性を保つために使用します。 ロックを使用すると、他のユーザーがデータを変更している最中にそのデータを読み取ったり、複数のユーザーが同時に同一のデータを変更したりする危険性を回避できます。 ロックを使用しないと、データベース内のデータが論理的に正しくなくなったり、そのデータに対して実行したクエリから予期しない結果が返されたりする可能性があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] の行ロックの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] オンライン ブックの「[!INCLUDE[ssDE](../../includes/ssde_md.md)]のロック」を参照してください。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)  
  
  
