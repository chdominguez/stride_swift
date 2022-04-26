# SwiftStride

This is a Swift adaptation of STRIDE. It is meant to be used with Swift projects as a Package dependency.

For more information about the original implementation, visit the GitHub repo from MDAnalysis.

https://github.com/MDAnalysis/stride


## Installation 

Add the URL of this repository to your Xcode Project.

`https://github.com/chdominguez/stride_swift.git`

### Import

To use the module import SwiftStride

`import SwiftStride`

## Usage

SwiftStride will return an amino acid array containing the prediction data (secondary structure, angles...) provided a file URL pointing to a PDB file.

`let aa = Stride.predict(from: fileURL)`

You can apply Stride arguments via the `arguments` parameter. Please refer to the original repository for documentation about the valid arguments.

`let arg = ["-o", "-h"]`

`let aa = Stride.predict(from: fileURL, arguments: arg)`

The output can be printed to the console setting to `true` the showReport parameter

`let aa = Stride.predict(from: fileURL, showReport: true)`

The returned array `aa` is filled with Residue types from which you can extract the predicted information.

```
public struct Residue {
    // Default values:
    public let type: AminoAcid
    public let structure: SecondaryStructure
    public let phi: Float
    public let psi: Float
    public let area: Float
}
```

## About STRIDE:

STRIDE [1] is a program to recognize secondary structural elements  in
proteins from  their atomic coordinates. It performs the same task as
DSSP by Kabsch and Sander [2] but utilizes both hydrogen bond  energy
and  mainchain  dihedral angles rather than hydrogen bonds alone. It
relies on database-derived recognition parameters with the
crystallographers' secondary structure definitions as a standard-of-
truth. Please see Frishman and Argos [1] for detailed description  of
the algorithm.

 1.  Frishman,D    & Argos,P. (1995) Knowledge-based secondary structure
     assignment.  Proteins:  structure,    function and genetics, 23,   
     566-579.

 2.  Kabsch,W. & Sander,C. (1983)  Dictionary  of  protein  secondary
     structure:       pattern   recognition   of    hydrogen-bonded      and
     geometrical features. Biopolymers,    22: 2577-2637.
