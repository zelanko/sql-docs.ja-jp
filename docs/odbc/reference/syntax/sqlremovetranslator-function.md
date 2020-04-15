---
title: SQL ムーストランスレータ関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveTranslator
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveTranslator
helpviewer_keywords:
- SQLRemoveTranslator function [ODBC]
ms.assetid: c6feda49-0359-4224-8de9-77125cf2397b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 348d2c5da0731ba88ccd4dd6406d3754890f7906
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301789"
---
# <a name="sqlremovetranslator-function"></a>SQLRemoveTranslator 関数
**適合 性**  
 バージョン導入: ODBC 3.0  
  
 **まとめ**  
 **SQLRemoveTranslator は**、システム情報の Odbcinst.ini セクションからトランスレータに関する情報を削除し、トランスレータのコンポーネント使用率カウントを 1 減らします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLRemoveTranslator(  
     LPCSTR    lpszTranslator,  
     LPDWORD   lpdwUsageCount);  
```  
  
## <a name="arguments"></a>引数  
 *lpszトランスレータ*  
 [入力]システム情報の Odbcinst.ini キーに登録されているトランスレータの名前。  
  
 *使用法のカウント*  
 [出力]この関数が呼び出された後の変換プログラムの使用回数。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。 この関数が呼び出されたときにシステム情報にエントリが存在しない場合、この関数は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQLRemoveトランスレータ**が FALSE を返すと、関連付けられた*\*pfErrorCode*値を取得するには **、SQLInstallerError**を呼び出します。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|レジストリにコンポーネントが見つかりません|レジストリに存在しないか、レジストリに見つからなかったため、インストーラはトランスレータ情報を削除できませんでした。|  
|ODBC_ERROR_INVALID_NAME|無効なドライバまたはトランスレータ名|*lpsz トランスレータ*引数が無効でした。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|コンポーネントの使用カウントをインクリメントまたはデクリメントできませんでした|インストーラーは、ドライバーの使用カウントを減らすに失敗しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **SQL 除去トランスレータ関数**[を補完](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)し、システム情報のコンポーネントの使用カウントを更新します。 この関数は、セットアップ アプリケーションからのみ呼び出す必要があります。  
  
 **SQLRemoveTranslator は**、コンポーネントの使用カウントを 1 減算します。 コンポーネントの使用カウントが 0 になると、システム情報のトランスレーター項目が削除されます。 変換プログラムのエントリは、システム情報の次の場所に、変換プログラム名の下にあります。  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
 **実際には**、どのファイルも削除しません。 呼び出し元のプログラムは、ファイルの削除とファイル使用量カウントの維持を担当します。 コンポーネントの使用カウントとファイル使用量カウントがゼロに達した後にのみ、ファイルは物理的に削除されます。 コンポーネント内の一部のファイルは削除でき、その他のファイルは、ファイル使用量カウントをインクリメントした他のアプリケーションによって使用されているかどうかによって、削除されません。  
  
 **SQLRemoveトランスレータ**は、アップグレード プロセスの一部としても呼び出されます。 アプリケーションがアップグレードを実行する必要があることを検出し、以前にドライバをインストールした場合は、ドライバを削除してから再インストールする必要があります。 **まず、** コンポーネントの使用カウントを減算するために呼び出**す必要があります**。 アプリケーションセットアッププログラムは、古いファイルを新しいファイルに物理的に置き換える必要があります。 ファイルの使用数は変わらず、古いバージョンのファイルを使用する他のアプリケーションは新しいバージョンを使用します。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|変換プログラムのインストール|[トランスレータ](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|
