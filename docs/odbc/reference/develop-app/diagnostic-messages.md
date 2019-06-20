---
title: 診断メッセージ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic messages messages
- error messages [ODBC], diagnostic messages
- diagnostic messages [ODBC]
ms.assetid: 98027871-9901-476e-a722-ee58b7723c1f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 883cd29d8628f1e9270ae95a772c4d116b896710
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63034919"
---
# <a name="diagnostic-messages"></a>診断メッセージ
各 sqlstate は、診断メッセージが返されます。 同じ SQLSTATE は多くの場合、さまざまなメッセージの数が返されます。 たとえば、SQL 構文でほとんどのエラーの SQLSTATE 42000 (構文エラーまたはアクセス違反) が返されます。 ただし、各構文エラーは、別のメッセージで説明を取得する可能性があります。  
  
 サンプル診断メッセージは、SQLSTATEs 付録 A には各関数でのテーブル内のエラー列に表示されます。 ドライバーは、これらのメッセージを返すことができますはどのようなメッセージは、渡されたデータ ソースによって返される可能性が高くなります。  
  
 一般に、アプリケーションは、SQLSTATE、ネイティブ エラー コードと、ユーザーに診断メッセージを表示します。 これにより、ユーザーと、サポート担当者が問題の原因を特定します。 メッセージに埋め込まれているコンポーネントの情報は、これを行う場合に特に役立ちます。  
  
 診断メッセージは、データ ソースとドライバー、ゲートウェイ、およびドライバー マネージャーなどの ODBC 接続のコンポーネントから取得します。 通常、データ ソースは ODBC を直接サポートしています。 その結果、ODBC 接続のコンポーネントは、データ ソースからメッセージを受信した場合は、メッセージのソースとしてデータ ソースを識別する必要があります。 メッセージを受信したコンポーネントとして識別、自体もする必要があります。  
  
 エラーまたは警告のソースがコンポーネント自体の場合は、診断メッセージはこれを説明する必要があります。 したがって、メッセージのテキストには、2 つの異なる形式があります。 エラーとデータ ソースで発生しない警告では、診断メッセージは、この形式を使用する必要があります。  
  
 **[** *vendor-identifier* **][** *ODBC-component-identifier* **]** *component-supplied-text*  
  
 エラーとデータ ソースで発生する警告は、診断メッセージは、この形式を使用する必要があります。  
  
 **[** *vendor-identifier* **][** *ODBC-component-identifier* **][** *data-source-identifier* **]** *data-source-supplied-text*  
  
 次の表では、各要素の意味を示します。  
  
|要素|説明|  
|-------------|-------------|  
|*仕入先 id*|エラーまたは警告が発生したか、データ ソースから直接、エラーまたは警告を受信するコンポーネントのベンダーを識別します。|  
|*ODBC コンポーネントの識別子*|エラーまたは警告が発生したか、データ ソースから直接、エラーまたは警告を受信するコンポーネントを識別します。|  
|*data-source-identifier*|データ ソースを識別します。 ファイル ベースのドライバーでは、これは通常、ファイル形式など Xbase [1] の DBMS ベースのドライバーでは、これは、DBMS の製品です。|  
|*component-supplied-text*|ODBC コンポーネントによって生成されます。|  
|*data-source-supplied-text*|データ ソースによって生成されます。|  
  
 [1] この場合は、ドライバーは、ドライバーとデータ ソースの両方として機能しています。  
  
 角かっこ ( **[ ]** ) メッセージに含める必要があるし、省略可能な項目が示されていません。
