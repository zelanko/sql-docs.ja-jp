---
title: PDOStatement::getAttribute |Microsoft Docs
ms.custom: ''
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 41d0cca3-8556-4573-bb90-8e9402d9379f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b3c1c79da6d1efc51778cb09eb6bd2fed460576a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66799152"
---
# <a name="pdostatementgetattribute"></a>PDOStatement::getAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

定義済みの PDOStatement 属性またはカスタム ドライバー属性の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
mixed PDOStatement::getAttribute( $attribute );  
```  
  
#### <a name="parameters"></a>パラメーター  
$*attribute*: PDO::ATTR_* または PDO::SQLSRV_ATTR_\* 定数のいずれかの整数。 サポートされている属性で設定できる属性[pdostatement::setattribute](../../connect/php/pdostatement-setattribute.md)、pdo::sqlsrv_attr_direct_query (詳細については、次を参照してください[直接ステートメント実行と準備されたステートメントの実行で。PDO_SQLSRV ドライバー](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md))、pdo::attr_cursor および pdo::sqlsrv_attr_cursor_scroll_type (詳細については、次を参照してください。[カーソルの種類 (PDO_SQLSRV ドライバー)](../../connect/php/cursor-types-pdo-sqlsrv-driver.md))。  
  
## <a name="return-value"></a>戻り値  
成功した場合、定義済みの PDO 属性またはカスタム ドライバー属性用の (複合) 値を返します。 エラーが発生した場合は NULL を返します。  
  
## <a name="remarks"></a>Remarks  
例については、「 [PDOStatement::setAttribute](../../connect/php/pdostatement-setattribute.md) 」を参照してください。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
