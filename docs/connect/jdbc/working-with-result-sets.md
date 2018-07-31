---
title: 結果セットの操作 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4fc4b1c6-3075-4ad7-9244-865d9ede7ae6
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b2797c9ce000d687550ee50c27fdc51524f86c6
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38060305"
---
# <a name="working-with-result-sets"></a>結果セットの処理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースに格納されているデータを操作するための方法の 1 つに、結果セットを使用する方法があります。 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は、[SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトを介して結果セットの使用をサポートします。 SQLServerResultSet オブジェクトを使用することで、SQL ステートメントまたはストアド プロシージャから返されたデータを取得し、必要に応じてデータを更新し、データをデータベースに戻して保持できます。  
  
 また、SQLServerResultSet オブジェクトは、このオブジェクトのデータ行間を移動したり、オブジェクトに含まれるデータを取得または設定したり、基になるデータベースの変更に対するさまざまなレベルの応答性を確立したりするためのメソッドを提供します。  
  
> [!NOTE]  
>  変更に対する応答性など、結果セットの管理の詳細については、次を参照してください。 [JDBC ドライバーでの結果セットの管理](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)します。  
  
 このセクションのトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースに含まれているデータを操作するために結果セットを使用できるさまざまな方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|[説明]|  
|-----------|-----------------|  
|[結果セットのデータ サンプルの取得](../../connect/jdbc/retrieving-result-set-data-sample.md)|結果セットを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースからデータを取得し、表示する方法について説明します。|  
|[結果セットのデータ サンプルの変更](../../connect/jdbc/modifying-result-set-data-sample.md)|結果セットを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースのデータを挿入、取得、および変更する方法について説明します。|  
|[結果セットのデータ サンプルのキャッシング](../../connect/jdbc/caching-result-set-data-sample.md)|結果セットを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースから大量のデータを取得し、そのデータがクライアント上でキャッシュされる方法を制御する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [サンプル JDBC Driver アプリケーション](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
