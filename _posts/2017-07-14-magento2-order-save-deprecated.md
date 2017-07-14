---
layout: post
title: Magento2 $order->save() deprecated
description: Small post about order save in magento2
---
Im Magento2 Core findet man noch einige solcher Code-Stellen:

```php
$order = $clonedOrder;
$order->setId(
    null
)->setCustomerEmail(
    'customer@example.com'
)->setBillingAddress(
    $billingAddress
)->setShippingAddress(
    $shippingAddress
)->setPayment(
    $payment
);
$order->save();
```

Obwohl die **save function** von _src/vendor/magento/framework/Model/AbstractModel.php_ deprecated ist 
([siehe hier](https://github.com/magento/magento2/blame/develop/lib/internal/Magento/Framework/Model/AbstractModel.php#L637)) 
wird sie noch viel verwendet.

Da stellt sich natürlich die Frage wie das nun im Magento2 in Zukunft gemacht werden soll?

Vielleicht eher so?
```php
$order = $this->orderRepository->get($order->getId());
$order->setOrderExported(1);
$returnSimpleXmlObject = $this->readResultOrderXml($result);
$order->addStatusHistoryComment($this->createMessageString($returnSimpleXmlObject));
$this->orderRepository->save($order);
```

Anstelle von _$oder->save();_ sollte sich also jeder das **\Magento\Sales\Api\OrderRepositoryInterface** anschauen und 
wie dieses in Magento2 verwendet wird. Das Magento Core Team arbeitet daran, dass nur noch das OrderRepositoryInterface
in Zukunft Verwendung findet.
