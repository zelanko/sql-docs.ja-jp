---
title: データ ソース | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC]
- data sources [ODBC], about data sources
ms.assetid: 4ae44fa2-0b9b-4e19-ab45-c1dc93b68406
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b7e464963471b0cad41c5b93d50507d0fa9bf96
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306513"
---
# <a name="data-sources"></a>ソリューション エクスプローラー
*データ ソース*は、単にデータのソースです。 ファイル、DBMS 上の特定のデータベース、またはライブ データ フィードを指定できます。 データは、プログラムと同じコンピューター上に置くか、ネットワーク上の別のコンピューター上に配置されている可能性があります。 たとえば、データ ソースは、OS/2® オペレーティング システム上で実行されている Oracle DBMS であり、Novell® Netware によってアクセスされます。ゲートウェイを介してアクセスされる IBM DB2 DBMS。サーバー ディレクトリ内の Xbase ファイルのコレクション。またはローカルの Microsoft ® Access データベース ファイルを作成します。  
  
 データ ソースの目的は、データにアクセスするために必要なすべての技術情報 (ドライバー名、ネットワーク アドレス、ネットワーク ソフトウェアなど) を 1 か所に集めて、ユーザーに対して非表示にすることです。 ユーザーは、給与、在庫、および従業員を含むリストを参照し、リストから [給与] を選択し、給与データの場所やアプリケーションの取得方法を知らなくても、アプリケーションを給与データに接続できる必要があります。  
  
 データ*ソース*という用語は、類似した用語と混同しないでください。 このマニュアルでは *、DBMS*または*データベース*はデータベース プログラムまたはエンジンを参照します。 パーソナル コンピュータ上で実行するように設計された*デスクトップ データベース*と、クライアント/サーバーの状況で実行するように設計されたサーバー*データベースと、* スタンドアロン のデータベース エンジンと豊富な SQL とトランザクション サポートが特徴のサーバー データベースの間で、さらに区別されます。 *データベース*は、ディレクトリ内の Xbase ファイルのコレクションや SQL Server 上のデータベースなど、特定のデータの集合を参照します。 これは一般に、このマニュアルの他の場所で使用されている*用語カタログ*、または以前のバージョンの ODBC では*修飾子*と同じです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [データ ソースの種類](../../odbc/reference/types-of-data-sources.md)  
  
-   [データ ソースの使用](../../odbc/reference/using-data-sources.md)  
  
-   [データ ソースの例](../../odbc/reference/data-source-example.md)
