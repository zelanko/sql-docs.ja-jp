---
title: 付録 - 1 (AccessToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 00665e16-2990-4bfc-8e17-d97ca9fb4999
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: c97b1f8c85b9d90d9e580f2b2cc4c517855e3abf
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773108"
---
# <a name="appendix---1-accesstosql"></a>付録 - 1 (AccessToSQL)
SSMA コンソール コマンド ライン オプションの簡易表示:  
  
|Sl. 不可。|スイッチ|必須/省略可能|引数を切り替える|指定できる値|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|はい|scriptfile|有効な XML ファイルの名前。<br /><br />スクリプトの定義ファイルのコンソールです。|  
|2|-v/変数|いいえ|variablevaluefile|有効な XML ファイルの名前。 変数をスクリプト ファイルで使用する場合は、このファイルを指定する必要があります。|  
|3|-c/serverconnection|いいえ|serverconnectionfile|有効な XML ファイルの名前。 このファイルには、サーバーの接続情報が含まれています。|  
|4|-x/xmloutput|いいえ|xmloutputfile|このオプションでは、XML 形式でのコンソール出力を示します。 このオプションが指定されていない場合、既定の出力はテキスト形式です。<br /><br />Xmloutputfile が指定されていない場合、XML 出力は STDOUT に送られます。<br /><br />Xmloutputfile は、XML 形式で、コンソール出力の書き込み先となるファイルの名前です。|  
|5|-l/log|いいえ|logfile|有効なファイル名。|  
|6|-e/projectenvironment|いいえ|projectenvironmentfolder|SSMA プロジェクト環境ファイルを含む有効なフォルダー名です。|  
|7|-p/securepassword|いいえ|-、/add {< server_id > [,... n] &#124; すべて} – c &#124; serverconnection < サーバー接続ファイル > [-v &#124; 変数 < 変数値ファイル >] [-o/上書き]<br /><br />または<br /><br />-、/add {< server_id > [,... n] &#124; すべて} – s&#124; スクリプト < スクリプト ファイル > [-v &#124; 変数 < 変数値ファイル >] [-o/上書き]<br /><br />– r/削除 {< server_id > [,... n] &#124; すべて}<br /><br />-l/一覧表示<br /><br />– e/エクスポート {< サーバー id > [,... n] &#124; すべて} < 暗号化パスワード - ファイル ><br /><br />– i/インポート {< サーバー id > [,... n] &#124; すべて} < 暗号化パスワード ファイルに >|指定した場合、このオプションをその他のオプションと組み合わされていない必要があります。<br /><br />サーバー id: {string} サーバーの一意の ID が提供されます。<br /><br />ファイル サーバーに接続: サーバーの定義ファイル (serverconnectionfile または scriptfile)。<br /><br />変数値ファイル: クエリ変数の定義ファイルし、ファイル サーバーに接続で使用します。<br /><br />暗号化されたパスワード ファイル: ユーザーが指定したパス フレーズを使用して暗号化のサーバーのパスワード ファイルです。|  
|8|-?|いいえ|該当なし|該当なし|  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (アクセス) を実行します。](http://msdn.microsoft.com/en-us/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
