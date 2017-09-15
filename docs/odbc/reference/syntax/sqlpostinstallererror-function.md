---
title: "SQLPostInstallerError 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLPostInstallerError
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPostInstallerError
helpviewer_keywords:
- SQLPostInstallerError function [ODBC]
ms.assetid: 4c60d827-b2d2-4f27-b220-daa9e1fcdd8d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f7d3a6bec7c12e271c073d5665c0a4e9b227ceef
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlpostinstallererror-function"></a>SQLPostInstallerError 関数
**準拠**  
 バージョンが導入されています。 ODBC 3.0  
  
 **概要**  
 **SQLPostInstallerError**ドライバーまたはトランスレーター セットアップ ライブラリ エラーを報告するためのメカニズムを提供、 **ConfigDriver**、 **ConfigDSN**、および**ConfigTranslator**インストーラー エラー キューに機能します。 アプリケーションは、この API を使用しないでください。使用する**SQLInstallerError**エラーを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
RETCODE SQLPostInstallerError(  
     DWORD    fErrorCode,  
     LPSTR    szErrorMsg);  
```  
  
## <a name="arguments"></a>引数  
 *fErrorCode*  
 [入力]インストーラーのエラー コード。  
  
 *後*  
 [入力]エラー メッセージ テキストです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS や SQL_ERROR です。  
  
## <a name="diagnostics"></a>診断  
 **SQLPostInstallerError**自体のエラー値が通知されません。 エラーがインストーラー エラー キューに正常にポストされたかどうか (を使用して取得できる**SQLInstallerError**)、SQL_SUCCESS が返されます。 場合、SQL_ERROR が返されますの値、 *dwErrorCode*引数は、指定されたインストーラーのエラー コードのいずれかではありません。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|追加、変更、またはドライバーを削除します。|[ConfigDriver](../../../odbc/reference/syntax/configdriver-function.md)|  
|追加、変更、またはデータ ソースの削除|[ConfigDSN](../../../odbc/reference/syntax/configdsn-function.md)|  
|翻訳オプションの設定|[ConfigTranslator](../../../odbc/reference/syntax/configtranslator-function.md)|
