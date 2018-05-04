---
title: JDBC ドライバーのデータ型を理解する |Microsoft ドキュメント
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
ms.assetid: 7802328d-4d23-4775-9573-4169b127d258
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e54821f18403b03fe5dd4042cd19324e0beb09fa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-the-jdbc-driver-data-types"></a>JDBC ドライバーのデータ型について
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] JDBC の基本と高度なデータ型を使用する Java アプリケーション内での使用をサポートしている[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のデータベースとして。  
  
 JDBC の型システムの間の変換を仲介する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型と Java 言語型およびオブジェクト。 JDBC の型は、SQL-92 および SQL-99 の型をモデルにしています。 JDBC ドライバーは、JDBC 仕様を満たし、予測可能性と柔軟性の適切なバランスを維持できるように設計されています。  
  
 このセクションのトピックでは、基本型および高度な型の使用方法と、データ型を他のデータ型に変換する方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[基本データ型の使用](../../connect/jdbc/using-basic-data-types.md)|JDBC の基本データ型について説明します。 これには、結果セット、パラメーター化クエリ、およびストアド プロシージャを使用してデータ型を操作する方法の例が含まれます。|  
|[java.sql.Time の値をサーバーに送信する方法の構成](../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)|JDBC Driver での日付の生成方法について説明します。|  
|[高度なデータ型の使用](../../connect/jdbc/using-advanced-data-types.md)|JDBC の高度なデータ型について説明します。|  
|[データ型の違いについて](../../connect/jdbc/understanding-data-type-differences.md)|JDBC ドライバーのさまざまなデータ型の違いについて説明します。|  
|[データ型変換について](../../connect/jdbc/understanding-data-type-conversions.md)|getter メソッドおよび setter メソッドを使用するときに、データ型の変換を処理する方法について説明します。|  
|[各国語文字セットのサポート](../../connect/jdbc/national-character-set-support.md)|National Character Set の型のサポートについて説明します。|  
|[XML データのサポート](../../connect/jdbc/supporting-xml-data.md)|SQLXML インターフェイスについて説明します。 リレーショナル データベースに XML データを読み書きする方法についても説明、 **SQLXML** Java データ型。|  
|[ラッパーとインターフェイス](../../connect/jdbc/wrappers-and-interfaces.md)|持つインターフェイスについて説明します、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]固有のメソッドとアプリケーション サーバーで、クラスのプロキシを作成できる定数についても説明のサポート、java.sql.Wrapper インターフェイスです。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
