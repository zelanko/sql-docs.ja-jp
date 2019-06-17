---
title: 付録 - 1 (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 2d22766d-ff09-420d-ae7c-13b443e28bd0
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 20cda553190074236f8cf50bb719a5c1e019e416
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63253307"
---
# <a name="appendix---1-mysqltosql"></a>付録 - 1 (MySQLToSQL)
SSMA コンソールのコマンド ライン オプションを簡単に確認します。  
  
|Sl. No.|スイッチ|必須/省略可能|スイッチ引数|使用できる値|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|[はい]|scriptfile|有効な XML ファイルの名前。<br /><br />スクリプトの定義ファイルのコンソールです。|  
|2|-v/変数|いいえ|variablevaluefile|有効な XML ファイルの名前。<br /><br />変数は、スクリプト ファイルで使用される、このファイルを指定する必要があります。|  
|3|-c/serverconnection|いいえ|serverconnectionfile|有効な XML ファイルの名前。<br /><br />このファイルには、サーバーの接続情報が含まれています。|  
|4|-x/xmloutput|いいえ|xmloutputfile|このオプションでは、XML 形式でコンソール出力を示します。 このオプションが指定されていない場合、既定の出力は、テキスト形式では。<br /><br />Xmloutputfile が指定されていない場合、XML 出力は STDOUT に送られます。<br /><br />Xmloutputfile では、XML 形式でコンソール出力の書き込み先ファイルの名前です。|  
|5|-l/log|いいえ|logfile|有効なファイル名。|  
|6|-e/projectenvironment|いいえ|projectenvironmentfolder|SSMA プロジェクト環境ファイルを含む有効なフォルダー名。|  
|7|-p/securepassword|いいえ|-a/add {<server_id> [,...n] &#124; all} -c&#124;serverconnection  <server-connection-file> [-v&#124;variable <variable-value-file>] [-o/overwrite]<br /><br />または<br /><br />-a/add {<server_id> [,...n] &#124; all} -s&#124;script <script-file> [-v&#124;variable <variable-value-file>] [-o/overwrite]<br /><br />-r/remove {<server_id> [, ...n] &#124; all}<br /><br />-l/list<br /><br />-e/export {<server-id> [, ...n] &#124; all} <encrypted-password -file><br /><br />-i/import {<server-id> [, ...n] &#124; all} <encrypted-password-file>|指定した場合、このオプションをその他のオプションと組み合わされていない必要があります。<br /><br />サーバー id:サーバー {文字列} に指定された一意の ID<br /><br />サーバー接続ファイル: サーバーの定義ファイル (serverconnectionfile または scriptfile)。<br /><br />変数の値のファイル:変数の定義ファイルし、サーバー接続ファイルで使用します。<br /><br />暗号化されたパスワード ファイルに:サーバー パスワード ファイルがユーザーが指定したパス フレーズを使用して暗号化することをお勧めします。|  
|8|-?|いいえ|該当なし|該当なし|  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (MySQL) の実行](https://msdn.microsoft.com/e3e9f7e4-0619-4861-a202-3d5d39953b26)  
  
