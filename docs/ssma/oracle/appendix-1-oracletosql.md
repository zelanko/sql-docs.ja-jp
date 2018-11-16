---
title: 付録 - 1 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: e01f8be5-ce68-4c9f-bd13-d65e73a16470
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 2539ac90fcce2dd1d5b30384c07bac620d809f0a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51668241"
---
# <a name="appendix---1-oracletosql"></a>付録 - 1 (OracleToSQL)
SSMA コンソールのコマンド ライン オプションを簡単に確認します。  
  
|Sl. No.|スイッチ|必須/省略可能|スイッチ引数|使用できる値|  
|-----------|----------|-------------|-------------------|--------------------|  
|1|-s/script|はい|scriptfile|有効な XML ファイルの名前。<br /><br />スクリプトの定義ファイルのコンソールです。|  
|2|-v/変数|いいえ|variablevaluefile|有効な XML ファイルの名前。<br /><br />変数は、スクリプト ファイルで使用される、このファイルを指定する必要があります。|  
|3|-c/serverconnection|いいえ|serverconnectionfile|有効な XML ファイルの名前。<br /><br />このファイルには、サーバーの接続情報が含まれています。|  
|4|-x/xmloutput|いいえ|xmloutputfile|このオプションでは、XML 形式でコンソール出力を示します。 このオプションが指定されていない場合、既定の出力は、テキスト形式では。<br /><br />XML の出力に出力 xmloutputfile が指定されていない場合`STDOUT`します。<br /><br />Xmloutputfile では、XML 形式でコンソール出力の書き込み先ファイルの名前です。|  
|5|-l/log|いいえ|logfile|有効なファイル名。|  
|6|-e/projectenvironment|いいえ|projectenvironmentfolder|SSMA プロジェクト環境ファイルを含む有効なフォルダー名。|  
|7|-p/securepassword|いいえ|-、/add {< server_id > [,... n] &#124; すべて} – c &#124; serverconnection < サーバー接続ファイル > [-v &#124; 変数 < 変数値ファイル >] [-o/上書き]<br /><br />または<br /><br />-、/add {< server_id > [,... n] &#124; すべて} – s&#124; スクリプト < スクリプト ファイル > [-v &#124; 変数 < 変数値ファイル >] [-o/上書き]<br /><br />– r/削除 {< server_id > [,... n] &#124; すべて}<br /><br />-l/一覧表示<br /><br />– e/エクスポート {< サーバー id > [,... n] &#124; すべて} < 暗号化パスワード - ファイル ><br /><br />– i/インポート {< サーバー id > [,... n] &#124; すべて} < 暗号化パスワード ファイルに >|指定した場合、このオプションをその他のオプションと組み合わされていない必要があります。<br /><br />サーバー id: {string} サーバーの一意の ID が提供されます。<br /><br />サーバー接続ファイル: サーバーの定義ファイル (serverconnectionfile または scriptfile)。<br /><br />変数値のファイル: これは変数の定義ファイルであり、サーバー接続ファイルで使用します。<br /><br />暗号化されたパスワード ファイル: これは、サーバーのパスワード ファイルをユーザーが指定したパス フレーズを使用して暗号化します。|  
|8|-?|いいえ|該当なし|該当なし|  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (Oracle) の実行](https://msdn.microsoft.com/7228ccba-c69f-4b4c-8664-01a2750183c5)  
  
