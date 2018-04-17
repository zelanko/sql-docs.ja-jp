---
title: トランスレーター セットアップ Dll |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4974722410319634e6bc4c18fd8bdea7d89c9cb1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="translator-setup-dlls"></a>トランスレーター セットアップ Dll
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 DLL を含む変換プログラムのセットアップ、 **ConfigTranslator**関数で、変換プログラムの既定のオプションを返します。 必要に応じて、ユーザーにこの情報メッセージが表示されます。 この関数の詳細については、次を参照してください。[セットアップ DLL の API リファレンス](../../../odbc/reference/syntax/setup-dll-api-reference.md)です。  
  
 トランスレーター セットアップ DLL は、変換プログラムの開発者によって書き込まれます。 変換プログラムの一部にすることができます、または別の DLL。
