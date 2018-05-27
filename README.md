# A DOM Element factory with vanilla Javascript (ES6)
There are three basic parts to any DOM element: the type of element it is, any attributes we need the element to have, and any children of the element. Knowing this, we can start to write our factory function. knowing this, it is easy to create a constructor function of elements.

#### Function

	const elFactory = (type, attributes, ...children) => {
		const el = document.createElement(type);
    	for (key in attributes) {
        	el.setAttribute(key, attributes[key]);
    	};
		children.forEach(child => {
			if (typeof child === 'string') {
				el.appendChild(document.createTextNode(child));
			} else {
				el.appendChild(child);
			}
		});
		return el;
	}

#### Use 

	const markup = elFactory(
		'div', { class: 'my-component' }, elFactory('span', {}, 'Hello World!'),
		'My first element'
	);

#### Result

	<div class='my-component'>
  		<span>Hello World!</span> My first element!
	</div>
