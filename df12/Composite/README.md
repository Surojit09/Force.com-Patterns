Example implementation of Composite Design Pattern in Apex demonstrating representation of below expressions.

    1 AND 2
    1 OR (2 AND 3)
    (1 AND 2) OR ((3 OR 4) AND 5)

## Usage

    //1 OR (2 AND 3)
    Expression expr = (new OrComposite())
        .add(new Variable('1'))
        .add((new AndComposite())
            .add(new Variable('2'))
            .add(new Variable('3'))
        )
        .set('1',false)
        .set('2',true)
        .set('3',false);

    System.debug(expr.evaluate());
    //FALSE OR (TRUE AND FALSE) => FALSE

    expr.set('3',true);

    System.debug(expr.evaluate());
    //FALSE OR (TRUE AND TRUE) => TRUE