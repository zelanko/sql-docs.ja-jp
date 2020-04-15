---
title: DBMS ベースドライバ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drivers [ODBC], DBMS-based drivers
- DBMS-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
ms.assetid: e2208ee0-4cd6-4f0d-bb71-a0b54f7d9330
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e7b7b153d0b0cb0a3e6a3d738908b0039b95679
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306488"
---
# <a name="dbms-based-drivers"></a>DBMS ベースのドライバー
DBMS ベースのドライバは、Oracle や SQL Server などのデータ ソースで使用され、ドライバが使用するスタンドアロン のデータベース エンジンを提供します。 これらのドライバーは、スタンドアロン エンジンを介して物理データにアクセスします。つまり、エンジンに対して SQL ステートメントを送信し、エンジンから結果を取得します。  
  
 DBMS ベースのドライバは既存のデータベース エンジンを使用するため、通常はファイル ベースのドライバよりも簡単に書き込みできます。 DBMS ベースのドライバは、ODBC 呼び出しをネイティブ API 呼び出しに変換することで簡単に実装できますが、結果的に低速なドライバーになります。 DBMS ベースのドライバを実装する優れた方法は、ネイティブ API が行う通常のデータ ストリーム プロトコルを使用することです。 たとえば、SQL Server ドライバーは、データベース ライブラリ (SQL Server のネイティブ API) ではなく、TDS (SQL Server のデータ ストリーム プロトコル) を使用する必要があります。 この規則の例外は、ODBC がネイティブ API である場合です。 たとえば、Watcom SQL は、アプリケーションと同じマシン上に存在し、ドライバーとして直接読み込まれるスタンドアロン エンジンです。  
  
 DBMS ベースのドライバは、データ ソースがサーバとして機能するクライアント/サーバ構成でクライアントとして機能します。 ほとんどの場合、クライアント (ドライバー) とサーバー (データ ソース) は異なるコンピューターに存在しますが、どちらもマルチタスクオペレーティング システムを実行している同じコンピューターに存在する可能性があります。 3 つ目の可能性は、ドライバーとデータ ソースの間に位置する*ゲートウェイ*です。 ゲートウェイとは、ある DBMS が別の DBMS のように見えるソフトウェアです。 たとえば、SQL Server を使用するように作成されたアプリケーションは、マイクロディシジョンウェア DB2 ゲートウェイを介して DB2 データにアクセスすることもできます。この製品は、DB2 が SQL Server のように見えるようにします。  
  
 次の図は、DBMS ベースのドライバの 3 種類の構成を示しています。 最初の構成では、ドライバーとデータ ソースは同じコンピューターに存在します。 2 番目の例では、ドライバーとデータ ソースは異なるコンピューターに存在します。 3 番目の方法では、ドライバとデータ ソースは異なるマシンに存在し、ゲートウェイはその間に位置し、さらに別のマシンに存在します。  
  
 ![DBMS&#45;ベースのドライバの 3 つの構成](../../odbc/reference/media/pr07.gif "pr07")
