---
title: スクリプト言語での ADO の使用 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- scripting languages [ADO]
- ADO, scripting languages
ms.assetid: 76fc4d00-0c9f-422b-af5c-af6ed8fb29d8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6b322dacbf85ec24b58e315ecbbf9d547d1481f9
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926488"
---
# <a name="using-ado-with-scripting-languages"></a>スクリプト言語で ADO を使用する
スクリプト環境では、ADO を使用して、サーバー側のスクリプトによってデータを公開できます。 このシナリオでは、ADO、基になる OLE DB プロバイダー、および特定のデータストアを参照するために必要なその他のコンポーネントが、インターネットインフォメーションサービス (IIS) を実行しているサーバーにインストールされます。 ADO は、Active Server ページ (ASP) を使用して、HTML を生成できるスクリプトで参照されるコンポーネントです。たとえば、のようになります。 この HTML コンテンツは、HTTP 経由でクライアントの Web ブラウザーに渡すことができます。 スクリプトを使用すると、Web ページからサーバー側スクリプトにアクションを送信して、特定のデータを更新、スキャン、または表示できるようにすることができます。  
  
 Web ページで ActiveX オブジェクトを使用する前に、オブジェクトがスクリプトに対して安全かどうかを把握しておくことが重要です。 オブジェクトがスクリプトに対して安全であると見なされる場合は、コントロールがユーザーのコンピューターで有害な操作を実行できないため、ユーザーの承認を要求することなく実行できます。 次の表に、ADO オブジェクトの一覧と、それらがスクリプトに対して安全かどうかを示します。  
  
|Object|スクリプトに対して安全ですか?|  
|------------|-------------------------|  
|ADO 接続|はい|  
|ADO コマンド|いいえ|  
|ADO パラメーター|いいえ|  
|ADO レコードセット|はい|  
|ADO レコード|はい|  
|ADO ストリーム|はい|  
|ADO エラーです。|いいえ|  
|ADOX カタログ|いいえ|  
|ADOX CellSet|いいえ|  
|RDS DataControl|はい|  
|RDS の領域スペース|はい|  
|RDS DataFactory|いいえ|  
  
 次の表に、Windows DAC/MDAC に含まれるプロバイダーと、スクリプトに対して安全かどうかを示します。  
  
|プロバイダー|スクリプトに対して安全ですか?|  
|--------------|-------------------------|  
|図形|はい|  
|Persist|はい|  
|リモート|はい|  
|OLE DB Provider for SQL Server (SQLOLEDB)|いいえ|  
|OLE DB Provider for ODBC (MSDASQL)|いいえ|  
  
## <a name="odbc-data-sources"></a>ODBC データ ソース  
 スクリプトとスクリプト以外の ADO コードの大きな違いの1つは、ODBC データソース (使用されている場合) です。 非スクリプトアプリケーションの場合は、ODBC データソースアドミニストレーターでユーザー DSN を作成できます。 IIS で実行されているスクリプトの場合は、システム DSN を作成する必要があります。そうしないと、作成したデータソースがスクリプトによって認識されません。 これは、microsoft IIS を介して ODBC 用の Microsoft OLE DB Provider を使用する ADO スクリプトアプリケーションに適用されます。  
  
## <a name="referencing-the-ado-library"></a>ADO ライブラリの参照  
 スクリプト言語には適用されません。  
  
## <a name="handling-events"></a>イベントの処理  
 スクリプト言語には適用されません。  
  
 次のトピックには、スクリプト言語での ADO の使用に関する具体的な情報が含まれています。  
  
-   [VBScript での ADO プログラミング](../../../ado/guide/appendixes/vbscript-ado-programming.md)  
  
-   [JScript での ADO プログラミング](../../../ado/guide/appendixes/jscript-ado-programming.md)  
  
## <a name="see-also"></a>参照  
 [Microsoft ActiveX データオブジェクト (ADO)](../../../ado/microsoft-activex-data-objects-ado.md)   
 [Microsoft Visual Basic での ADO の使用](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-basic.md)   
 [Microsoft Visual C++ での ADO の使用](../../../ado/guide/appendixes/using-ado-with-microsoft-visual-c.md)   
