---
title: 付録 - 1 (OracleToSQL) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
caps.latest.revision: 15
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 4afeb0ab89e38f9d0b5533bcc56405a0dbdb3cbf
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33038329"
---
# <a name="appendix---1-oracletosql"></a>付録 - 1 (OracleToSQL)
SSMA コンソール コマンド ライン オプションの簡易表示:  
  
|Sl です。 不可。|スイッチ|必須/省略可能|引数を切り替える|指定できる値|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|はい|scriptfile|有効な XML ファイルの名前。<br /><br />スクリプトの定義ファイルのコンソールです。|  
|2|-v/変数|いいえ|variablevaluefile|有効な XML ファイルの名前。<br /><br />変数をスクリプト ファイルで使用する場合は、このファイルを指定する必要があります。|  
|3|-c/serverconnection|いいえ|serverconnectionfile|有効な XML ファイルの名前。<br /><br />このファイルには、サーバーの接続情報が含まれています。|  
|4|-x/xmloutput|いいえ|xmloutputfile|このオプションでは、XML 形式でのコンソール出力を示します。 このオプションが指定されていない場合、既定の出力はテキスト形式です。<br /><br />Xmloutputfile が指定されていない場合は、XML に出力されます`STDOUT`です。<br /><br />Xmloutputfile は、XML 形式で、コンソール出力の書き込み先となるファイルの名前です。|  
|5|-l/log|いいえ|logfile|有効なファイル名。|  
|6|-e/projectenvironment|いいえ|projectenvironmentfolder|SSMA プロジェクト環境ファイルを含む有効なフォルダー名です。|  
|7|-p/securepassword|いいえ|-、/add {< server_id > [,... n] &#124; すべて} – c&#124; serverconnection < サーバー接続ファイル > [-v&#124; 変数 < 変数値ファイル >] [-o/上書き]<br /><br />または<br /><br />-、/add {< server_id > [,... n]&#124: すべて} – s&#124; スクリプト < スクリプト ファイル > [-v &#124; 変数 < 変数値ファイル >] [-o/上書き]<br /><br />– r/削除 {< server_id > [,... n] &#124; すべて}<br /><br />-l/一覧表示<br /><br />– e/エクスポート {< サーバー id > [,... n] &#124; すべて} < 暗号化パスワード - ファイル ><br /><br />– i/インポート {< サーバー id > [,... n] &#124; すべて} < 暗号化パスワード ファイルに >|指定した場合、このオプションをその他のオプションと組み合わされていない必要があります。<br /><br />サーバー id: {string} サーバーの一意の ID が提供されます。<br /><br />ファイル サーバーに接続: サーバーの定義ファイル (serverconnectionfile または scriptfile)。<br /><br />変数値ファイル: クエリ変数の定義ファイルし、ファイル サーバーに接続で使用します。<br /><br />暗号化されたパスワード ファイル: ユーザーが指定したパス フレーズを使用して暗号化のサーバーのパスワード ファイルです。|  
|8|-?|いいえ|該当なし|該当なし|  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (Oracle) を実行します。](http://msdn.microsoft.com/en-us/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
