---
title: ドライバー マネージャーの役割 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- diagnostic information [ODBC], driver manager error checking
- SQLGetDiagField function [ODBC], driver manager
- SQLGetDiagRec function [ODBC], driver manager
- ODBC driver manager [ODBC]
- diagnostic information [ODBC], SqlGetDiagRec
- driver manager [ODBC], error checking
ms.assetid: 7b861c82-357e-4590-8074-45136e9ed15e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5985144c212988d8c35553f710f3edd40e6bfc1
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="role-of-the-driver-manager"></a>ドライバー マネージャーの役割
ドライバー マネージャーでは、生成された状態レコードを返す最終的な順序を決定します。 具体的には、どのレコードが最高のランクがありが最初に返されるを決定します。 ドライバーは、生成された状態レコードを順序付けします。 状態レコードは、ドライバー マネージャーとドライバーの両方によって送信されたが場合、は、ドライバー マネージャーを順序付ける担当します。 詳細については、次を参照してください。[状態レコードのシーケンス](../../../odbc/reference/develop-app/sequence-of-status-records.md)です。  
  
 ドライバー マネージャーは、できるだけ多くのエラー チェックを可能な限りを行われます。 これにより、同じエラーのチェックからすべてのドライバーが保存されます。 たとえば、関数の引数がなど不連続値、数を受け付ける*操作*で**SQLSetPos**、ドライバー マネージャーでは、指定した値が有効なことを確認します。  
  
 次のセクションでは、ドライバー マネージャーによって確認条件の種類について説明します。 すべてを網羅; これらの目的ではありません。ドライバー マネージャーを返します SQLSTATEs の完全な一覧は、各関数の「診断」を参照してください。ドライバー マネージャーによって行われた各チェックの説明は"(DM)"で始まる また、状態遷移内のテーブルを参照してください[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md); かっこで囲まれたエラーが、ドライバー マネージャーによって検出されました。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [引数の値のチェック](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [状態遷移の確認](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [一般的なエラー チェック](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [ドライバー マネージャーのエラーと警告の確認](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)
