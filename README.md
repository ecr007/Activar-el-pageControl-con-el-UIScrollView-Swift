# Activar-el-pageControl-con-el-UIScrollView-Swift

```swift
// Al objeto del page control se le asigna un target
objPageControl.addTarget(self, action: #selector(pageControlDidChange(_:))), for: .valueChanged)

@objc private func pageControlDidChange(_ sender: UIPageControl){
	let current = sender.currentPage

	// Funcion para desplazar el scroll
	scrollObject.setContentOffset(CGPoint(x: CGFloat(current) * view.frame.size.width, y: 0), animated: true);
}

// Para mover los puntos del pageControl con debemos llamar a los delegados de scroll

scrollObject.delegate = self

// Especificamente se llama al delegado ::: para pasarle la info al pageControl

func scrollViewDidScroll(_ scrollView: UIScrollView){
	pageControl.currentPage = Int( floorf( Float( scrollView.contentOffset.x ) / Float( scrollView.frame.size.width ) ) )
}
```
