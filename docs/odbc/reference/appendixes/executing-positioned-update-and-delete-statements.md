---
title: "Update ステートメントと Delete ステートメントを実行する配置されている |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- positioned deletes [ODBC]
- cursor library [ODBC], positioned update or delete
- positioned updates [ODBC]
- ODBC cursor library [ODBC], positioned update or delete
ms.assetid: 1d64f309-2a6e-4ad1-a6b5-e81145549c56
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 78bdb77c8aa4d9351e040b97d9690bb09374856d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="executing-positioned-update-and-delete-statements"></a>位置指定更新ステートメントと Delete ステートメントを実行します。
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 アプリケーションで、データのブロックをフェッチした後、 **SQLFetchScroll**、更新したり、ブロック内のデータを削除したりします。 位置指定更新または削除、アプリケーションを実行します。  
  
1.  呼び出し**SQLSetPos**に更新または削除する行にカーソルを移動します。  
  
2.  位置指定更新または次の構文で delete ステートメントを構築します。  
  
     **更新***テーブル名*  
  
     **設定***列識別子*  **=**  {*式*&#124; です。**NULL**}  
  
     [**、** *列識別子*  **=**  {*式*&#124; です。**NULL**}]  
  
     **WHERE CURRENT OF** *カーソル名*  
  
     **DELETE FROM** *テーブル名* **WHERE CURRENT OF** *カーソル名*  
  
     構築する最も簡単な方法、**設定**位置指定の update ステートメントの句は列ごとにパラメーター マーカーを使用して更新し、使用する**SQLBindParameter**これらの行セットのバッファーをバインドする、更新する行。 この場合、パラメーターの C データ型は、行セットのバッファーの C データ型と同じなります。  
  
3.  位置指定の update ステートメントを実行する場合は、現在の行の行セットのバッファーを更新します。 位置指定更新ステートメントを正常に実行するには後、は、カーソル ライブラリは、現在の行に各列からそのキャッシュを値をコピーします。  
  
    > [!CAUTION]  
    >  アプリケーションによって、位置指定の update ステートメントを実行する前の行セットのバッファーが正しく更新されない場合、キャッシュ内のデータされません正しい、ステートメントが実行された後にします。  
  
4.  位置指定更新または削除ステートメントがカーソルに関連付けられているステートメントよりも別のステートメントを使用して実行します。  
  
    > [!CAUTION]  
    >  **場所**を任意の行を識別する、別の行を特定または複数の行を識別する、現在の行を識別する、カーソル ライブラリで構築された句が失敗します。 詳細については、次を参照してください。[検索ステートメントを構築する](../../../odbc/reference/appendixes/constructing-searched-statements.md)です。  
  
 配置されているすべての更新プログラムおよび delete ステートメントがカーソル名を必要とします。 カーソル名を指定するには、アプリケーションが呼び出す**SQLSetCursorName**カーソルが開かれる前にします。 アプリケーションが使用するには、ドライバーによって生成されるカーソル名を呼び出す**SQLGetCursorName**カーソルが開かれています。  
  
 ライブラリが位置指定更新を実行するカーソルより後または delete ステートメント、状態配列、バッファーの行セット、および、カーソル ライブラリで保持されるキャッシュには、次の表に示すように値が含まれています。  
  
|使用するステートメント|行の状態配列内の値します。|内の値<br /><br /> バッファーの行セット|内の値<br /><br /> キャッシュ バッファー|  
|--------------------|-------------------------------|----------------------------------|---------------------------------|  
|位置指定更新を行う|SQL_ROW_UPDATED|新しい値 [1]|新しい値 [1]|  
|位置指定削除|SQL_ROW_DELETED|古い値|古い値|  
  
 [1] で、アプリケーションは、位置指定更新ステートメントを実行する前に、行セットのバッファー内の値を更新する必要があります。位置指定の update ステートメントを実行するは、カーソル ライブラリは、行セットのバッファーでのキャッシュに値をコピーします。

