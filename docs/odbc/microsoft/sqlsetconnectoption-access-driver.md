---
title: 接続オプション (アクセス ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLSetConnectOption
- SQLSetConnectOption function [ODBC], Access Driver
ms.assetid: 58399bc4-d0b1-4eaa-a474-c92b2d5855ea
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8e5f15575d34031d9886219af5677b4fc5f1d5aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301535"
---
# <a name="sqlsetconnectoption-access-driver"></a>SQLSetConnectOption (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|オプション|解説|  
|-------------|-------------|  
|SQL_ACCESS_MODE|fOption SQL_ACCESS_MODEは、SQL_MODE_READ_ONLYまたはSQL_MODE_READ_WRITEに設定できます。 ただし、SQL_ACCESS_MODEがSQL_MODE_READ_ONLYに設定されている場合、ドライバーは更新を防止しません。|  
|SQL_AUTOCOMMIT|Access ドライバを使用する場合、SQL_AUTOCOMMIT オプションは、トランザクション[1] をサポートしているため、SQL_AUTOCOMMIT_ONまたはSQL_AUTOCOMMIT_OFFに設定できます。|  
|SQL_CURRENT_QUALIFIER|サポートされています。|  
|SQL_LOGIN_TIMEOUT|サポートされていません。|  
|SQL_OPT_TRACE|サポートされています。|  
|SQL_OPT_TRACEFILE|サポートされています。|  
|SQL_PACKET_SIZE|サポートされていません。|  
|SQL_QUIET_MODE|サポートされていません。|  
|SQL_TRANSLATE_DLL|サポートされていません。|  
|SQL_TRANSLATION_OPTION|サポートされていません。|  
|SQL_TXN_ISOLATION|SQL_TXN_ISOLATIONは常にSQL_TXN_READ_COMMITTEDです。|  
  
 [1] アトミック トランザクションは、Access ドライバではサポートされていません。 Microsoft Access ドライバを使用してトランザクションをコミットする場合、トランザクションがコミットされた時点から値がディスクに書き込まれるまでの間に、限られた遅延が発生します。 この遅延は、Microsoft Jet エンジンに固有の遅延によって決まります。 PageTimeout オプションがその値より下に設定されている場合でも、ページタイムアウトは最小値より小さくなります。 その結果、遅延中に変更が行われる可能性があるため、コミットされたデータが安定しているという保証はありません。
