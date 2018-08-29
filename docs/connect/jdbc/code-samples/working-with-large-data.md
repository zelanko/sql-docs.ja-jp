---
title: 大規模なデータを扱う |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5b93569f-eceb-4f05-b49c-067564cd3c85
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 728e86f155a1bb61c7fe900f5e536eed991c206a
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786850"
---
# <a name="working-with-large-data"></a>大きなデータの処理

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

JDBC ドライバーは、サーバー カーソルのオーバーヘッドを発生させることなく、あらゆる種類の大きな値のデータを取得できるアダプティブ バッファリングをサポートします。 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] でアダプティブ バッファリングを使用すると、ステートメントの実行結果を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から取得する処理が、すべて一度にではなく、アプリケーションの必要に応じて行われます。 また、アプリケーションからアクセスできなくなった結果は、ドライバーによって直ちに破棄されます。  
  
[!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] JDBC Driver バージョン 1.2 のバッファリング モードの既定値は "**full**" でした。 アプリケーションで、接続プロパティを使用するか、[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトの [setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md) メソッドを使用して、"responseBuffering" 接続プロパティを "**adaptive**" に設定しなかった場合、サーバーから結果全体を一度に読み取るという動作になっていました。 アダプティブ バッファリングの動作をアプリケーションに実装するには、明示的に "responseBuffering" 接続プロパティを "**adaptive**" に設定する必要があります。  
  
**adaptive** 値はバッファリング モードの規定値であり、JDBC ドライバーは、必要に応じて最小限のデータをバッファリングします。 アダプティブ バッファリングの使用に関する詳細については、次を参照してください。[アダプティブ バッファリングを使用して](../../../connect/jdbc/using-adaptive-buffering.md)します。  
  
このセクションのトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースから大きな値のデータを取得するための、さまざまな方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
| トピック                                                                                                                         | [説明]                                                              |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [大きなデータを読み取るサンプル](../../../connect/jdbc/code-samples/reading-large-data-sample.md)                                               | SQL ステートメントを使用して大きな値のデータを取得する方法について説明します。       |
| [ストアド プロシージャで大きなデータを読み取るサンプル](../../../connect/jdbc/code-samples/reading-large-data-with-stored-procedures-sample.md) | 大きな CallableStatement OUT パラメーター値を取得する方法について説明します。 |
| [大きなデータを更新するサンプル](../../../connect/jdbc/code-samples/updating-large-data-sample.md)                                             | データベース内の大きな値のデータを更新する方法について説明します。                |
  
## <a name="see-also"></a>参照

[サンプル JDBC Driver アプリケーション](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
  