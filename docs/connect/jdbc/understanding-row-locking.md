---
title: 行ロックについて |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e2bb0038320ccefe0e143ca7c18fbf7e117c4a75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47719660"
---
# <a name="understanding-row-locking"></a>行ロックについて

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の行ロックを使用します。 これらには、データベースへの変更を複数のユーザーが同時に行う際のコンカレンシー制御が実装されています。 既定では、トランザクションとロックは接続ごとに管理されます。 たとえば、アプリケーションで 2 つの JDBC 接続が開かれている場合、一方の接続で取得したロックをもう一方の接続と共有することはできません。 どちらの接続でも、もう一方の接続によって保持されているロックと競合するロックは取得できません。

> [!NOTE]  
> 行ロックの使用時にはフェッチ バッファー内のすべての行がロックされるため、フェッチ サイズを非常に大きく設定すると、コンカレンシーに影響を与える可能性があります。

ロックは、トランザクションの整合性とデータベースの一貫性を保つために使用します。 ロックを使用すると、他のユーザーがデータを変更している最中にそのデータを読み取ったり、複数のユーザーが同時に同一のデータを変更したりする危険性を回避できます。 ロックを使用しないと、データベース内のデータが論理的に正しくなくなったり、そのデータに対して実行したクエリから予期しない結果が返されたりする可能性があります。

> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の行ロックの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「[!INCLUDE[ssDE](../../includes/ssde_md.md)]のロック」を参照してください。

## <a name="see-also"></a>参照

[JDBC ドライバーによる結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)
